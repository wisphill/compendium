#golang

```table-of-contents
```
### GC and Tricolor algorithm
- All objects in the HEAP are started as WHITE.
- If the object is reachable, haven't been scanned > GREY
- If the object is reachable, fully scanned all children of their graph > BLACK
- unreachable objects: Object in the HEAP and there are no references to it and it should be WHITE after the **marking** phase
- Write barrier: additional code be added at the compiled time with the condition {{ *If the WHITE object suddenly has a reference (impacted by other goroutines) during marking phase, it will be marked to GREY and wait to be scanned* }}
- BLACK objects are never be scanned anymore in the same GC cycle > so we need the Write barrier to make sure the WHITE objects are never be cleared and all children of them are scanned as well. 
- Sweep phase: Sweep all WHITE objects.
- STW: Cleanup stack of goroutines (local stack variables, pointers), and turn on/off Write barrier. Write Barrier only protects objects in the HEAPs.
```js-engine
const scenarios = {
  on: [
    { title: 'Start of mark phase', message: 'All heap objects are white. The object graph contains GC roots → A, GC roots → B, and A → C.', nodes: { A: 'white', B: 'white', C: 'white' }, edges: ['root-a', 'root-b', 'a-c'] },
    { title: 'GC progress before mutation', message: 'A is gray, B is already black, and C is still white. A still points to C.', nodes: { A: 'gray', B: 'black', C: 'white' }, edges: ['root-a', 'root-b', 'a-c'] },
    { title: 'Move C from A to B (barrier on)', message: 'The barrier shades C gray, then the mutator moves the reference: A no longer points to C, B now points to C. GC scans A, so A becomes black.', nodes: { A: 'black', B: 'black', C: 'gray' }, edges: ['root-a', 'root-b', 'b-c'] },
    { title: 'Drain C from the mark queue', message: 'C is gray because of the barrier, so GC scans it and turns it black. C safely survives this cycle.', nodes: { A: 'black', B: 'black', C: 'black' }, edges: ['root-a', 'root-b', 'b-c'] }
  ],
  off: [
    { title: 'Start of mark phase', message: 'All heap objects are white. The object graph contains GC roots → A, GC roots → B, and A → C.', nodes: { A: 'white', B: 'white', C: 'white' }, edges: ['root-a', 'root-b', 'a-c'] },
    { title: 'GC progress before mutation', message: 'A is gray, B is already black, and C is still white. A still points to C.', nodes: { A: 'gray', B: 'black', C: 'white' }, edges: ['root-a', 'root-b', 'a-c'] },
    { title: 'Move C from A to B (barrier off)', message: 'The mutator moves the reference: A becomes black after scanning without C; B now points to C. C remains white because no barrier put it in the mark queue.', nodes: { A: 'black', B: 'black', C: 'white' }, edges: ['root-a', 'root-b', 'b-c'] },
    { title: 'Mark finishes without C', message: 'A and B are black. B will not be scanned again, so C is still white even though B → C exists.', nodes: { A: 'black', B: 'black', C: 'white' }, edges: ['root-a', 'root-b', 'b-c'] },
    { title: 'Sweep reclaims white C', message: 'C is still white, so sweep reclaims it even though B → C exists. This is the bug the write barrier prevents.', nodes: { A: 'black', B: 'black', C: 'lost' }, edges: ['root-a', 'root-b', 'b-c'] }
  ]
};

let mode = 'on';
let step = 0;
const root = document.createElement('div');
root.className = 'write-barrier-demo';

const node = (name, x, y, color, caption) => {
  const targetStep = 0;
  return `<g class="node ${color}" transform="translate(${x} ${y})">
    <circle r="76"></circle>
    <text class="node-label" y="13">${name}</text>
    <foreignObject x="-76" y="-76" width="152" height="152">
      <button xmlns="http://www.w3.org/1999/xhtml" class="node-hit" data-node="${targetStep}" aria-label="Show ${name}'s state"></button>
    </foreignObject>
    <text class="caption" y="120">${caption}</text>
    ${color === 'lost' ? '<text class="cross" x="110" y="-55">×</text>' : ''}
  </g>`;
};

const colorLabel = (color) => color === 'lost' ? 'Unmarked' : color[0].toUpperCase() + color.slice(1);

function render() {
  const states = scenarios[mode];
  const state = states[step];
  root.innerHTML = `
    <style>
      .write-barrier-demo { max-width: 640px; margin: 1.25rem auto; color: var(--text-normal); }
      .write-barrier-demo button { font: inherit; cursor: pointer; }
      .write-barrier-demo .header, .write-barrier-demo .toolbar, .write-barrier-demo .controls { display: flex; align-items: center; justify-content: space-between; gap: 16px; }
      .write-barrier-demo h2 { margin: 0; font-size: 1.65em; }
      .write-barrier-demo .switch { display: flex; padding: 3px; border-radius: 999px; background: var(--background-secondary); }
      .write-barrier-demo .toggle { border: 0; border-radius: 999px; padding: 7px 19px; background: transparent; color: var(--text-muted); }
      .write-barrier-demo .toggle.selected { background: var(--background-primary); color: var(--text-normal); box-shadow: 0 1px 3px #0002; }
      .write-barrier-demo .toolbar { margin: 32px 8px 4px; font-size: 1.1em; }
      .write-barrier-demo .state-title { display: block; margin-top: 4px; color: var(--text-muted); font-size: .8em; font-weight: normal; }
      .write-barrier-demo .steps { color: var(--text-muted); }
      .write-barrier-demo svg { display: block; width: 100%; max-height: min(52vh, 470px); }
      .write-barrier-demo .root-box { fill: #dcfce7; stroke: #16a34a; stroke-width: 3; }
      .write-barrier-demo .root-label { fill: #166534; font-size: 34px; font-weight: 700; text-anchor: middle; dominant-baseline: middle; }
      .write-barrier-demo .edge { stroke: var(--text-faint); stroke-width: 6; opacity: .35; fill: none; }
      .write-barrier-demo .edge.active { stroke: #16a34a; opacity: 1; }
      .write-barrier-demo .node circle { fill: #273a52; stroke: #70819a; stroke-width: 6; }
      .write-barrier-demo .node.gray circle { fill: #9a6a14; stroke: #d79d32; }
      .write-barrier-demo .node.white circle { fill: var(--background-primary); stroke: #94a3b8; }
      .write-barrier-demo .node.white .node-label { fill: var(--text-muted); }
      .write-barrier-demo .node.lost circle { fill: #fecaca; stroke: #dc2626; stroke-dasharray: 11 8; }
      .write-barrier-demo .node.lost .node-label { fill: #17243a; }
      .write-barrier-demo .node-label { fill: #fff; font-size: 48px; font-weight: 700; text-anchor: middle; }
      .write-barrier-demo .caption { fill: var(--text-normal); font-size: 25px; text-anchor: middle; }
      .write-barrier-demo .cross { fill: #dc2626; font-size: 72px; font-weight: 700; }
      .write-barrier-demo .node-hit { width: 100%; height: 100%; border: 0; border-radius: 50%; background: transparent; }
      .write-barrier-demo .node-hit:hover { background: #ffffff20; }
      .write-barrier-demo .message { min-height: 2.8em; margin: 6px auto 18px; max-width: 760px; text-align: center; color: var(--text-muted); }
      .write-barrier-demo .controls { max-width: 600px; margin: 0 auto; }
      .write-barrier-demo .control { border: 1px solid var(--background-modifier-border); border-radius: 7px; padding: 7px 13px; background: var(--background-secondary); color: var(--text-normal); }
      .write-barrier-demo .control.primary { border-color: var(--interactive-accent); background: var(--interactive-accent); color: var(--text-on-accent); }
      .write-barrier-demo .control:disabled { opacity: .45; cursor: default; }
      .write-barrier-demo .dots { display: flex; gap: 8px; }
      .write-barrier-demo .dot { width: 10px; height: 10px; padding: 0; border: 0; border-radius: 50%; background: var(--text-faint); }
      .write-barrier-demo .dot.current { background: var(--interactive-accent); transform: scale(1.25); }
      .write-barrier-demo .hint { margin-top: 16px; text-align: center; color: var(--text-faint); font-size: .86em; }
    </style>
    <div class="header"><h2>Move C: A → B</h2><div class="switch"><button class="toggle ${mode === 'on' ? 'selected' : ''}" data-barrier="on">ON</button><button class="toggle ${mode === 'off' ? 'selected' : ''}" data-barrier="off">OFF</button></div></div>
    <div class="toolbar"><div><strong>Object graph</strong><span class="state-title">${state.title}</span></div><div class="steps">${mode.toUpperCase()} · Step ${step + 1}/${states.length}</div></div>
    <svg viewBox="0 0 900 700" role="img" aria-label="Interactive object graph moving C reference from A to B">
      <defs><marker id="arrow" markerWidth="12" markerHeight="12" refX="9" refY="3" orient="auto" markerUnits="strokeWidth"><path d="M0,0 L0,6 L9,3 z" fill="#16a34a"></path></marker></defs>
      ${state.edges.includes('root-a') ? '<line class="edge active" x1="405" y1="155" x2="255" y2="295" marker-end="url(#arrow)" />' : ''}
      ${state.edges.includes('root-b') ? '<line class="edge active" x1="495" y1="155" x2="645" y2="295" marker-end="url(#arrow)" />' : ''}
      ${state.edges.includes('b-c') ? '<line class="edge active" x1="625" y1="420" x2="485" y2="545" marker-end="url(#arrow)" />' : ''}
      ${state.edges.includes('a-c') ? '<line class="edge active" x1="270" y1="435" x2="430" y2="570" marker-end="url(#arrow)" />' : ''}
      <rect class="root-box" x="330" y="70" width="240" height="85" rx="27" /><text class="root-label" x="450" y="122">GC Roots</text>
      ${node('A', 240, 355, state.nodes.A, colorLabel(state.nodes.A))}
      ${node('B', 660, 355, state.nodes.B, colorLabel(state.nodes.B))}
      ${node('C', 450, 600, state.nodes.C, colorLabel(state.nodes.C))}
    </svg>
    <p class="message">${state.message}</p>
    <div class="controls"><button class="control" data-action="previous" ${step === 0 ? 'disabled' : ''}>← Previous</button><div class="dots">${states.map((_, index) => `<button class="dot ${index === step ? 'current' : ''}" data-step="${index}" aria-label="Go to step ${index + 1}"></button>`).join('')}</div><button class="control primary" data-action="next" ${step === states.length - 1 ? 'disabled' : ''}>Next →</button></div>
    <p class="hint">Click an object to jump to the step where it is examined.</p>`;

  root.querySelectorAll('[data-step]').forEach((button) => button.addEventListener('click', () => { step = Number(button.dataset.step); render(); }));
  root.querySelectorAll('[data-barrier]').forEach((button) => button.addEventListener('click', () => { mode = button.dataset.barrier; step = 0; render(); }));
  root.querySelectorAll('[data-node]').forEach((button) => button.addEventListener('click', () => { step = Number(button.dataset.node); render(); }));
  root.querySelector('[data-action="previous"]')?.addEventListener('click', () => { if (step > 0) { step--; render(); } });
  root.querySelector('[data-action="next"]')?.addEventListener('click', () => { if (step < scenarios[mode].length - 1) { step++; render(); } });
}

render();
return root;
```

### GMP in the Golang

```js-engine
const root = document.createElement('div');
root.className = 'gmp-diagram';
let mode = 'normal';
let zoom = 115;

function render() {
  const workStealing = mode === 'steal';
  const syscall = mode === 'syscall';
  const status = syscall
    ? 'M1 blocks in a syscall, so P1 detaches and M3 takes P1 to keep running goroutines.'
    : workStealing
      ? 'P2 has no local work, so it steals runnable goroutines from P1.'
      : 'M1 runs goroutines through P1; M2 runs goroutines through P2.';

  root.innerHTML = `
    <style>
      .gmp-diagram { max-width: none; margin: 1rem auto; color: var(--text-normal); }
      .gmp-diagram button { font: inherit; cursor: pointer; }
      .gmp-controls { display:flex; flex-wrap:wrap; gap:8px; margin:0 0 10px; }
      .gmp-controls button { border:1px solid var(--background-modifier-border); border-radius:7px; padding:6px 10px; background:var(--background-secondary); color:var(--text-normal); }
      .gmp-controls button.active { background:var(--interactive-accent); border-color:var(--interactive-accent); color:var(--text-on-accent); }
      .gmp-controls .gmp-zoom { margin-left:auto; display:flex; align-items:center; gap:6px; color:var(--text-muted); }
      .gmp-viewport { overflow:auto; max-height:760px; border:1px solid var(--background-modifier-border); border-radius:12px; background:var(--background-primary); }
      .gmp-status { min-height:1.5em; margin:0 0 9px; color:var(--text-muted); }
      .gmp-diagram svg { display:block; height:auto; background:var(--background-primary); }
      .gmp-title { font:700 34px system-ui,sans-serif; fill:var(--text-normal); }.gmp-h { font:700 21px system-ui,sans-serif; fill:#0f172a; }.gmp-t { font:600 15px system-ui,sans-serif; fill:#0f172a; }.gmp-s { font:500 12px system-ui,sans-serif; fill:#334155; }
      .gmp-g { fill:#bfdbfe; stroke:#0284c7; stroke-width:2; }.gmp-p { fill:#bbf7d0; stroke:#16a34a; stroke-width:3; }.gmp-m { fill:#fed7aa; stroke:#ea580c; stroke-width:3; }.gmp-q { fill:#ede9fe; stroke:#6d28d9; stroke-width:3; }.gmp-panel { fill:#fff; stroke:#94a3b8; stroke-width:2; }.gmp-edge { fill:none; stroke:#1e3a5f; stroke-width:3; marker-end:url(#gmp-arrow); }.gmp-green { fill:none; stroke:#15803d; stroke-width:3; marker-end:url(#gmp-green-arrow); }.gmp-hidden { opacity:.14; }.gmp-highlight { stroke:#2563eb; stroke-width:6; }
    </style>
    <div class="gmp-controls">
      <button class="${mode === 'normal' ? 'active' : ''}" data-mode="normal">Normal scheduling</button>
      <button class="${mode === 'steal' ? 'active' : ''}" data-mode="steal">Work stealing</button>
      <button class="${mode === 'syscall' ? 'active' : ''}" data-mode="syscall">Syscall handoff</button>
      <span class="gmp-zoom"><button data-zoom="out" aria-label="Zoom out">−</button><button data-zoom="reset">${zoom}%</button><button data-zoom="in" aria-label="Zoom in">+</button></span>
    </div>
    <p class="gmp-status">${status}</p>
    <div class="gmp-viewport"><svg viewBox="0 0 1000 650" style="width:${zoom * 10}px" role="img" aria-label="Interactive Go GMP scheduler model">
      <defs>
        <marker id="gmp-arrow" markerWidth="10" markerHeight="10" refX="8" refY="5" orient="auto"><path d="M0 0L10 5L0 10z" fill="#1e3a5f" /></marker>
        <marker id="gmp-green-arrow" markerWidth="10" markerHeight="10" refX="8" refY="5" orient="auto"><path d="M0 0L10 5L0 10z" fill="#15803d" /></marker>
      </defs>
      <text class="gmp-title" x="500" y="43" text-anchor="middle">Go GMP Scheduler Model</text>

      <g aria-label="Goroutines"><rect class="gmp-g" x="250" y="68" width="58" height="38" rx="9"/><rect class="gmp-g" x="320" y="68" width="58" height="38" rx="9"/><rect class="gmp-g" x="390" y="68" width="58" height="38" rx="9"/><rect class="gmp-g" x="600" y="68" width="58" height="38" rx="9"/><rect class="gmp-g" x="670" y="68" width="58" height="38" rx="9"/><rect class="gmp-g" x="740" y="68" width="58" height="38" rx="9"/><text class="gmp-t" x="279" y="93" text-anchor="middle">G1</text><text class="gmp-t" x="349" y="93" text-anchor="middle">G2</text><text class="gmp-t" x="419" y="93" text-anchor="middle">G3</text><text class="gmp-t" x="629" y="93" text-anchor="middle">G4</text><text class="gmp-t" x="699" y="93" text-anchor="middle">G5</text><text class="gmp-t" x="769" y="93" text-anchor="middle">G6</text></g>
      <path class="gmp-edge" d="M349 106V144H390V171"/><path class="gmp-edge" d="M699 106V144H688V171"/>

      <g aria-label="Global run queue"><rect class="gmp-q" x="20" y="185" width="190" height="175" rx="16"/><text class="gmp-h" x="115" y="216" text-anchor="middle">Global Run Queue</text><rect fill="#ddd6fe" x="37" y="237" width="156" height="45" rx="9"/><text class="gmp-t" x="65" y="266">G5</text><text class="gmp-t" x="110" y="266">G6</text><text class="gmp-h" x="158" y="266">…</text><text class="gmp-s" x="40" y="307">Shared overflow queue</text><text class="gmp-s" x="40" y="328">Used when local queues empty</text></g>

      <g aria-label="P1"><rect class="gmp-p" x="250" y="172" width="270" height="175" rx="16"/><text class="gmp-h" x="385" y="204" text-anchor="middle">P1 (Processor)</text><rect class="gmp-panel" x="267" y="220" width="160" height="80" rx="10"/><text class="gmp-t" x="347" y="246" text-anchor="middle">Local Run Queue</text><rect class="gmp-g" x="287" y="258" width="43" height="28" rx="7"/><rect class="gmp-g" x="342" y="258" width="43" height="28" rx="7"/><text class="gmp-s" x="308" y="277" text-anchor="middle">G1</text><text class="gmp-s" x="363" y="277" text-anchor="middle">G2</text><text class="gmp-s" x="385" y="325" text-anchor="middle">scheduler state · mcache · GC state</text></g>
      <g aria-label="P2"><rect class="gmp-p" x="590" y="172" width="270" height="175" rx="16"/><text class="gmp-h" x="725" y="204" text-anchor="middle">P2 (Processor)</text><rect class="gmp-panel" x="607" y="220" width="160" height="80" rx="10"/><text class="gmp-t" x="687" y="246" text-anchor="middle">Local Run Queue</text><rect class="gmp-g" x="663" y="258" width="43" height="28" rx="7"/><text class="gmp-s" x="685" y="277" text-anchor="middle">G4</text><text class="gmp-s" x="725" y="325" text-anchor="middle">scheduler state · mcache · GC state</text></g>
      <path class="gmp-edge" d="M210 268H250"/><path class="gmp-green ${workStealing ? '' : 'gmp-hidden'} ${workStealing ? 'gmp-highlight' : ''}" d="M520 254H590"/><text class="gmp-t ${workStealing ? '' : 'gmp-hidden'}" x="555" y="241" text-anchor="middle" fill="#15803d">steal G</text>

      <g aria-label="Machines"><rect class="gmp-m ${syscall ? 'gmp-hidden' : ''}" x="283" y="427" width="205" height="62" rx="15"/><text class="gmp-h" x="385" y="456" text-anchor="middle">M1</text><text class="gmp-t" x="385" y="478" text-anchor="middle">OS Thread</text><rect class="gmp-m" x="623" y="427" width="205" height="62" rx="15"/><text class="gmp-h" x="725" y="456" text-anchor="middle">M2</text><text class="gmp-t" x="725" y="478" text-anchor="middle">OS Thread</text>${syscall ? '<rect class="gmp-m" x="283" y="427" width="205" height="62" rx="15"/><text class="gmp-h" x="385" y="456" text-anchor="middle">M3</text><text class="gmp-t" x="385" y="478" text-anchor="middle">takes P1</text><rect x="300" y="504" width="170" height="29" rx="8" fill="#fee2e2" stroke="#dc2626"/><text class="gmp-s" x="385" y="524" text-anchor="middle">M1 blocked in syscall</text>' : ''}</g>
      <path class="gmp-green" d="M385 427V347"/><path class="gmp-green" d="M725 427V347"/>
      <rect fill="#e0e7ff" stroke="#4338ca" stroke-width="3" x="280" y="548" width="550" height="45" rx="13"/><text class="gmp-h" x="555" y="578" text-anchor="middle">OS Scheduler / Kernel</text><path class="gmp-edge" d="M385 489V548H470"/><path class="gmp-edge" d="M725 489V548H645"/>
      <text class="gmp-s" x="555" y="622" text-anchor="middle">GOMAXPROCS limits the number of Ps that can execute Go code simultaneously.</text>
    </svg></div>`;

  root.querySelectorAll('[data-mode]').forEach((button) => button.addEventListener('click', () => { mode = button.dataset.mode; render(); }));
  root.querySelectorAll('[data-zoom]').forEach((button) => button.addEventListener('click', () => {
    const action = button.dataset.zoom;
    zoom = action === 'in' ? Math.min(180, zoom + 15) : action === 'out' ? Math.max(70, zoom - 15) : 115;
    render();
  }));
}

render();
return root;
```

G: Goroutine (Unit of work), use small of context (few kbs)
M: OS Thread to pick up G. The Go runtime **requests to create M (OS Thread)**
P: **Logic resources of Go scheduler

**Mechanism**
1. **P contains GC state, Scheduler state**, **mcache** for quick allocation without asking OS.
2. Go scheduler determine which G can be proceeded by which M via P.
3. **Number of P = GOMAXPROCS**. 12 core CPU, P still can greater than 12, create more M, but it's costly for CPU to process, and not effective.
4. If M is processing G and **got blocking syscall**, such as a disk I/O. M can be released from **P(n)**, and another M will be assigned to process the **P(n)**
5. **Without P**, M always have to compete on the same global queue locks to get the G. (old model of Go)
6. If a G is still **waiting** no **blocking syscall**, another G in the same P still can be assigned to the same M. P is still stick with the same M.
7. At a time, **one M will be assigned to one P**, if not getting blocking syscall
