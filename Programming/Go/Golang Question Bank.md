---
flashcard_uid: 9732085c
cssclasses: true-recall-cards
parents:
  - "[[Golang]]"
---
#flashcards


**What is the entry point of an executable Go program?<span class="tr-accent-blue tr-tail-left"></span>**
<span class="tr-card-separator">??</span>
<span class="tr-card-answer">The `main` function in `package main`.</span>
<!-- true-recall: {"v":1,"id":"770c5b97-c550-41c9-919c-e1b73a8fb121","schedules":[{"updatedAt":1793588090555,"due":"2026-11-11T02:54:50.538Z","stability":8.2956,"difficulty":1,"reps":1,"lapses":0,"state":2,"lastReview":"2026-11-02T02:54:50.538Z","scheduledDays":9,"learningStep":0,"suspended":false,"createdAt":1793523989260}],"bases":{"dagoj9f7":{"front":"48f3a2eb5f22d149413190e25719c24e068c15209cbd22b154bd737f4fc56269","back":"59d04542a610b0925f496085ed0eceb4dbb780d95f9f2af9e92e5afa536f6a83","reversed":false}}} -->

**What is the difference between `var` and `:=`?<span class="tr-accent-mint tr-tail-right"></span>**
<span class="tr-card-separator">??</span>
<span class="tr-card-answer">`var` can be used at package or function scope; `:=` declares and initializes variables only inside functions.</span>
<!-- true-recall: {"v":1,"id":"b921b115-39d8-47bb-8bd6-fe15e6e2fe8a","schedules":[{"updatedAt":1793588971253,"due":"2026-11-05T03:09:31.234Z","stability":3.94605407,"difficulty":1,"reps":2,"lapses":0,"state":2,"lastReview":"2026-11-02T03:09:31.234Z","scheduledDays":3,"learningStep":0,"suspended":false,"createdAt":1793523989263}],"bases":{"dagoj9f7":{"front":"a429e094603419e210f514103cfbe05b8458b49b52df9d038f0dff36cf938caf","back":"b84159b5a710245e16370bd7845eec90c43dff9f93f9e337fc82ada29111ba07","reversed":false}}} -->

**What does `defer` do?<span class="tr-accent-coral tr-tail-left"></span>**
<span class="tr-card-separator">??</span>
<span class="tr-card-answer">It schedules a function call to run when the surrounding function returns.</span>
<!-- true-recall: {"v":1,"id":"d1b8d66e-92f1-4ab8-9642-ea0be4a8c797","schedules":[{"updatedAt":1793588953846,"due":"2026-11-06T03:09:13.833Z","stability":3.94605407,"difficulty":1,"reps":2,"lapses":0,"state":2,"lastReview":"2026-11-02T03:09:13.833Z","scheduledDays":4,"learningStep":0,"suspended":false,"createdAt":1793523989265}],"bases":{"dagoj9f7":{"front":"470d9dd2d4c925a52fe73603350dbb2f3ce2fe9993bc913bb7b1620c49252204","back":"df5be73d4810e20f2757a44e76280de3d8e12180860c9803c2b266d709ab4dd9","reversed":false}}} -->

**How does Go normally handle expected errors?<span class="tr-accent-purple tr-tail-right"></span>**
<span class="tr-card-separator">??</span>
<span class="tr-card-answer">Functions return an `error` value, which callers check explicitly.</span>
<!-- true-recall: {"v":1,"id":"afadbc0c-afa1-4ce4-8b68-dea7d2e39a28","schedules":[{"updatedAt":1793588105925,"due":"2026-11-10T02:55:05.908Z","stability":8.2956,"difficulty":1,"reps":1,"lapses":0,"state":2,"lastReview":"2026-11-02T02:55:05.908Z","scheduledDays":8,"learningStep":0,"suspended":false,"createdAt":1793523989266}],"bases":{"dagoj9f7":{"front":"a02e9014f99bc93869ef452fe892e1158c3bb847bad5bfbce2c42ff3841b662b","back":"3389bf6373828678c79e399f1927488654d2f7583908e8a83688d713b9c7d2d8","reversed":false}}} -->

## Types and collections

**What is the difference between an array and a slice in Go?<span class="tr-accent-amber tr-tail-left"></span>**
<span class="tr-card-separator">??</span>
<span class="tr-card-answer">An array has a fixed length that is part of its type; a slice is a descriptor containing a pointer into an underlying array, plus a length and capacity. Updating an existing slice element updates that backing array; the slice does not store a separate pointer for every element.</span>
<!-- true-recall: {"v":1,"id":"f4074afd-b992-43d3-8aec-7099f55a0ed9","schedules":[{"updatedAt":1793588068707,"due":"2026-11-09T02:54:28.689Z","stability":8.2956,"difficulty":1,"reps":1,"lapses":0,"state":2,"lastReview":"2026-11-02T02:54:28.689Z","scheduledDays":7,"learningStep":0,"suspended":false,"createdAt":1793523989268}],"bases":{"dagoj9f7":{"front":"3ef6fce7b9e4d05b900c204fdf80169f4c421ec816e846c488071daea85947e6","back":"fce551aed314e7740a7e0793b967810ae93b5a500376e4e933dacf094885f275","reversed":false}}} -->

**How do you test whether a key is present in a map?<span class="tr-accent-teal tr-tail-right"></span>**
<span class="tr-card-separator">??</span>
<span class="tr-card-answer">Use the comma-ok form: `value, ok := m[key]`.</span>
<!-- true-recall: {"v":1,"id":"7bf50c01-8cd6-4ce3-b970-b8f0a58c4a4f","schedules":[{"updatedAt":1793588128771,"due":"2026-11-08T02:55:28.751Z","stability":8.2956,"difficulty":1,"reps":1,"lapses":0,"state":2,"lastReview":"2026-11-02T02:55:28.751Z","scheduledDays":6,"learningStep":0,"suspended":false,"createdAt":1793523989270}],"bases":{"dagoj9f7":{"front":"bb0e27414b19fbe4ef6bc0d511c688694c2608bb6bfd3fc14f2c07e227dababd","back":"7a438099fa73cece1c0c0205bcf1a56234061f9c99533953b28f4f9bceafb8f6","reversed":false}}} -->

**What is a Go interface?<span class="tr-accent-coral tr-tail-left"></span>**
<span class="tr-card-separator">??</span>
<span class="tr-card-answer">A set of method signatures that a type satisfies implicitly by implementing those methods.</span>
<!-- true-recall: {"v":1,"id":"4a6378cf-7c9d-465c-9e67-8938c62fb23e","schedules":[{"updatedAt":1793547705722,"due":"2026-11-11T15:41:45.698Z","stability":8.2956,"difficulty":1,"reps":1,"lapses":0,"state":2,"lastReview":"2026-11-01T15:41:45.698Z","scheduledDays":10,"learningStep":0,"suspended":false,"createdAt":1793523989271}],"bases":{"dagoj9f7":{"front":"1f27b2cb7393d7f4dff54ffaf8d7abc1386eefe158e03a01b5f93e242fd617c8","back":"10a9e0d02ac0d5ab731356864fcb35d105c15ebfd426ce935e5375a7b1a3e049","reversed":false}}} -->

**When should you use a pointer receiver for a method?<span class="tr-accent-blue tr-tail-right"></span>**
<span class="tr-card-separator">??</span>
<span class="tr-card-answer">When the method must modify the receiver or copying the receiver would be expensive.</span>
<!-- true-recall: {"v":1,"id":"9b01b10f-139b-4e4d-9cd5-e543a985ff54","schedules":[{"updatedAt":1793588169359,"due":"2026-11-08T02:56:09.341Z","stability":8.2956,"difficulty":1,"reps":1,"lapses":0,"state":2,"lastReview":"2026-11-02T02:56:09.341Z","scheduledDays":6,"learningStep":0,"suspended":false,"createdAt":1793523989273}],"bases":{"dagoj9f7":{"front":"3a7fb211eb6dc2278788f537f268e3e4fef639a1e00e89b3642f0320bd019a17","back":"ab69dac568320f69adf91c0552cd0b2c336cfdcd0559c6dac67a4cc993996d34","reversed":false}}} -->

## Slices and memory

**What does a slice value contain, and why can two slices affect each other?<span class="tr-accent-purple tr-tail-left"></span>**
<span class="tr-card-separator">??</span>
<span class="tr-card-answer">A slice contains a pointer to its first backing-array element, a length, and a capacity. Slicing or assigning a slice copies that descriptor, not the elements, so slices that overlap the same backing array can observe each other's element writes.</span>
<!-- true-recall: {"v":1,"id":"b086ee3d-2f40-4023-b468-538e940e2270","schedules":[{"updatedAt":1793588345019,"due":"2026-11-02T02:59:05.019Z","stability":0,"difficulty":0,"reps":0,"lapses":0,"state":0,"lastReview":null,"scheduledDays":0,"learningStep":0,"suspended":false,"createdAt":1793588345019}],"bases":{"dagoj9f7":{"front":"bb5de0e7bc71bbf04530f541b58cce560686b1f650b6384ab6578f5488ec4437","back":"9817e68419d1556933f9283006705c08aa867384a3e4330a32c331f9318be360","reversed":false}}} -->

**What happens when `append` is called on a slice, and why must its result be assigned?<span class="tr-accent-mint tr-tail-right"></span>**
<span class="tr-card-separator">??</span>
<span class="tr-card-answer">If capacity remains, `append` writes into the existing backing array and returns a slice with a larger length. If not, it allocates a new backing array and copies the elements. In either case, use `s = append(s, x)` because the returned slice header may have a new length, capacity, and pointer.</span>
<!-- true-recall: {"v":1,"id":"45839e4a-e0e1-494e-b313-c53f64f3fc89","schedules":[{"updatedAt":1793588345021,"due":"2026-11-02T02:59:05.021Z","stability":0,"difficulty":0,"reps":0,"lapses":0,"state":0,"lastReview":null,"scheduledDays":0,"learningStep":0,"suspended":false,"createdAt":1793588345021}],"bases":{"dagoj9f7":{"front":"ad74458dffdb4ef158733ab740c0f6c72165220d79b7dfc57855d6d69f81ad2a","back":"dc3ce8a94c6c416e2ba267758c882fb5d52c0b9c4db8bcf3666751bfa24d5e20","reversed":false}}} -->

**How can a small subslice accidentally retain a large amount of memory?<span class="tr-accent-amber tr-tail-left"></span>**
<span class="tr-card-separator">??</span>
<span class="tr-card-answer">A subslice still points into the original backing array. Keeping `small := large[:10]` live can therefore keep all of `large` reachable. Copy the wanted data into a new slice, for example `small := append([]byte(nil), large[:10]...)`, when the original large buffer should be collectible.</span>
<!-- true-recall: {"v":1,"id":"0ce99f62-3146-438a-a91b-4dfdddc69cfe","schedules":[{"updatedAt":1793591161095,"due":"2026-11-07T03:46:01.072Z","stability":3.94605407,"difficulty":1,"reps":2,"lapses":0,"state":2,"lastReview":"2026-11-02T03:46:01.072Z","scheduledDays":5,"learningStep":0,"suspended":false,"createdAt":1793588345022}],"bases":{"dagoj9f7":{"front":"c9d082eaf1c015df0642fedae24579ae81a7fbea00cce45f316c779bf58ac1b2","back":"a2820be2299c7b05193129e182456ce4a0cf2096d7a68b57e15fddca4af52932","reversed":false}}} -->

**How can you prevent an `append` to a subslice from overwriting later elements of its backing array?<span class="tr-accent-teal tr-tail-right"></span>**
<span class="tr-card-separator">??</span>
<span class="tr-card-answer">Use a full slice expression to limit capacity: `sub := s[low:high:max]`. max = cap. Its length and capacity are both `n`, so an append requires allocate a new backing array instead of writing into `s[n:]`.</span>
<!-- true-recall: {"v":1,"id":"b9d1417e-71e6-4c01-a771-c45ed61d541a","schedules":[{"updatedAt":1793591082504,"due":"2026-11-02T03:54:42.464Z","stability":0.24668919,"difficulty":6.40211507,"reps":2,"lapses":0,"state":1,"lastReview":"2026-11-02T03:44:42.464Z","scheduledDays":0,"learningStep":1,"suspended":false,"createdAt":1793588345023}],"bases":{"dagoj9f7":{"front":"56cb27dc7d466c48cc51f1cf1d09f18fdf32a739635011e4df5b702dc3e533ac","back":"4c3d774d41bad2e5dab85c12d71107a97f37f388e181a441025626e39748293d","reversed":false}}} -->

**What is the difference between copying a slice header and copying its elements?<span class="tr-accent-coral tr-tail-left"></span>**
<span class="tr-card-separator">??</span>
<span class="tr-card-answer">Assignment such as `b := a` copies only the slice header, so `a` and `b` normally share storage. `copy(dst, src)` copies element values into an already allocated destination. For a standalone clone, use `b := append([]T(nil), a...)` or `b := slices.Clone(a)`.</span>
<!-- true-recall: {"v":1,"id":"0ae4df40-0eec-42b9-bc7e-61b300ffeccb","schedules":[{"updatedAt":1793588345024,"due":"2026-11-02T02:59:05.024Z","stability":0,"difficulty":0,"reps":0,"lapses":0,"state":0,"lastReview":null,"scheduledDays":0,"learningStep":0,"suspended":false,"createdAt":1793588345024}],"bases":{"dagoj9f7":{"front":"264084e60cbc903c6ba30ebb652e4f10d3b77ffa61a98603089ba7e4f947d35b","back":"82f90f30820b89319acad882cdd02872171df99eda2b51abcd87543ac6ea28d9","reversed":false}}} -->

## Garbage collection

**How does Go's garbage collector decide whether an object can be reclaimed?<span class="tr-accent-blue tr-tail-right"></span>**
<span class="tr-card-separator">??</span>
<span class="tr-card-answer">Go uses a concurrent, tracing garbage collector. Starting from roots such as goroutine stacks, global variables, and runtime-managed references, it marks reachable objects. Unreachable heap objects become eligible for reclamation; programmers do not explicitly free them.</span>
<!-- true-recall: {"v":1,"id":"cbddff68-c40e-4021-9ddc-4f0ce90216a5","schedules":[{"updatedAt":1793588345025,"due":"2026-11-02T02:59:05.025Z","stability":0,"difficulty":0,"reps":0,"lapses":0,"state":0,"lastReview":null,"scheduledDays":0,"learningStep":0,"suspended":false,"createdAt":1793588345025}],"bases":{"dagoj9f7":{"front":"e5f2eda51ba3d1a4e5265728bb462170d7eb709d1fa9f3723925b9d3331afc26","back":"08a66daa9f11195808715920f9ea61fa5da745d3614ab89d55fd591f77412ec2","reversed":false}}} -->

**Why does setting a slice element to its zero value matter after removing it?<span class="tr-accent-purple tr-tail-left"></span>**
<span class="tr-card-separator">??</span>
<span class="tr-card-answer">Reslicing shortens the visible length but does not erase the backing-array slot. If the element is a pointer, that hidden slot can keep the referenced object reachable. After shifting the remaining elements, clear the unused tail slot: `copy(s[i:], s[i+1:]); s[len(s)-1] = nil; s = s[:len(s)-1]`.</span>
<!-- true-recall: {"v":1,"id":"43e5b77e-d99f-46cf-864b-be179212e82c","schedules":[{"updatedAt":1793588345026,"due":"2026-11-02T02:59:05.026Z","stability":0,"difficulty":0,"reps":0,"lapses":0,"state":0,"lastReview":null,"scheduledDays":0,"learningStep":0,"suspended":false,"createdAt":1793588345026}],"bases":{"dagoj9f7":{"front":"fa4864c710ab7f3c9f86239a68eb09fbbe65c879cc7d8d02c48235c3812dd825","back":"eea49b38c33874c68eb02e56e52c715adee5c55f3cdf122fd11c9c113f059d2f","reversed":false}}} -->

**What is a common goroutine leak, and why will garbage collection not fix it?<span class="tr-accent-mint tr-tail-left"></span>**
<span class="tr-card-separator">??</span>
<span class="tr-card-answer">A goroutine blocked forever on a channel send, receive, lock, or I/O remains reachable through the runtime and its stack. Because it is still live, the garbage collector cannot reclaim it. Design cancellation with `context.Context`, ensure channel consumers exist, and make goroutines able to exit.</span>
<!-- true-recall: {"v":1,"id":"1366c5f8-2d97-42c0-a81f-12be49b97b54","schedules":[{"updatedAt":1793588358344,"due":"2026-11-02T02:59:18.344Z","stability":0,"difficulty":0,"reps":0,"lapses":0,"state":0,"lastReview":null,"scheduledDays":0,"learningStep":0,"suspended":false,"createdAt":1793588358344}],"bases":{"dagoj9f7":{"front":"3424b7085f274d96c4721c695340a5746baa10028c3c4c9e1aba380e75f60454","back":"584fa06e6a7919ced4e471fe58f2f34d0cd099d1fd9fb9040b7bf00ab8c707e5","reversed":false}}} -->

**When is `runtime.GC()` appropriate, and why is it rarely the cure for high memory use?<span class="tr-accent-amber tr-tail-right"></span>**
<span class="tr-card-separator">??</span>
<span class="tr-card-answer">Explicit GC is mainly for narrow, measured cases such as a batch job that has just released a known large temporary allocation. It cannot free reachable objects, can add latency and CPU cost, and may mask retention bugs. First use profiling to find references that are unintentionally keeping data alive.</span>
<!-- true-recall: {"v":1,"id":"9da01d97-64b7-499f-a801-7553b7866fe9","schedules":[{"updatedAt":1793588358345,"due":"2026-11-02T02:59:18.345Z","stability":0,"difficulty":0,"reps":0,"lapses":0,"state":0,"lastReview":null,"scheduledDays":0,"learningStep":0,"suspended":false,"createdAt":1793588358345}],"bases":{"dagoj9f7":{"front":"a2d355218b8a3def40e4ecdab2567beb15e01a62e2f5a2053683c9953dd2e0a4","back":"fd8ac16b564d0408696593a7d62d46ffa2ac7ae6683b9146865a5074323cdff9","reversed":false}}} -->

**What are the major phases of a Go garbage-collection cycle?<span class="tr-accent-teal tr-tail-left"></span>**
<span class="tr-card-separator">??</span>
<span class="tr-card-answer">Go performs a short stop-the-world setup, then concurrent marking while application goroutines run, followed by a short stop-the-world mark termination. It then sweeps unreachable heap spans, mostly concurrently, returning their storage for future allocations. The collector is non-moving GC type, so object addresses do not change during collection.</span>
<!-- true-recall: {"v":1,"id":"6dfd5e24-9bbb-4f0c-9497-d71b0bcd3f12","schedules":[{"updatedAt":1793591501542,"due":"2026-11-04T03:51:41.523Z","stability":2.3065,"difficulty":2.11121424,"reps":2,"lapses":0,"state":2,"lastReview":"2026-11-02T03:51:41.523Z","scheduledDays":2,"learningStep":0,"suspended":false,"createdAt":1793588719653}],"bases":{"dagoj9f7":{"front":"ce2bebe29502ed787940d0509a11af68677777f72eb34e2ca62b62cf5a14b5a5","back":"364c7d91b3d2b95b1c10d3bf755a379e0eced95bd5ec5ec11a233f75dbcffe03","reversed":false}}} -->

**How does tri-color marking model object reachability?<span class="tr-accent-coral tr-tail-right"></span>**
<span class="tr-card-separator">??</span>
<span class="tr-card-answer">At the start, reachable candidates are white. A discovered object becomes grey, meaning it is known but its pointer fields have not all been scanned. Scanning it marks its referenced objects and turns it black. When no grey work remains, white objects were not reached and are collectible.</span>
<!-- true-recall: {"v":1,"id":"5ddcaf59-fc44-4c54-8742-9704ad6b216d","schedules":[{"updatedAt":1793594327782,"due":"2026-11-02T04:48:47.756Z","stability":2.3065,"difficulty":2.11810397,"reps":1,"lapses":0,"state":1,"lastReview":"2026-11-02T04:38:47.756Z","scheduledDays":0,"learningStep":1,"suspended":false,"createdAt":1793588719654}],"bases":{"dagoj9f7":{"front":"8928510c3327f36d88c70947562534cf682c0285634bfaa82071cce4d8d8be88","back":"1ba51fcb95c66a41ff5882163bc268f3640071228713da1b47ad320c4730128a","reversed":false}}} -->

**Why is a write barrier needed during concurrent marking?<span class="tr-accent-blue tr-tail-left"></span>**
<span class="tr-card-separator">??</span>
<span class="tr-card-answer">Without a barrier, a running goroutine could change a pointer after the collector has scanned the relevant object. That can hide a live white object from the marker, which might then reclaim it incorrectly. The compiler inserts write-barrier code around heap pointer writes while marking is active to preserve the collector's reachability invariant.</span>
<!-- true-recall: {"v":1,"id":"b79a822b-3fae-455c-b6f1-2ea333729988","schedules":[{"updatedAt":1793588719656,"due":"2026-11-02T03:05:19.655Z","stability":0,"difficulty":0,"reps":0,"lapses":0,"state":0,"lastReview":null,"scheduledDays":0,"learningStep":0,"suspended":false,"createdAt":1793588719655}],"bases":{"dagoj9f7":{"front":"c72e82911f3631d50ede1591605595e6462c2abf466806d4fd995941378d4c6c","back":"677d254f032e64b4090eeee1e80ed8ba44867d90c152358b348983953395fd8a","reversed":false}}} -->

**What does Go's hybrid write barrier do conceptually?<span class="tr-accent-purple tr-tail-right"></span>**
<span class="tr-card-separator">??</span>
<span class="tr-card-answer">Conceptually, it shades the pointer being overwritten (a deletion barrier) and, while the current goroutine's stack is grey, shades the new pointer value (an insertion barrier). Shading makes the object available for marking. This prevents a mutator from creating an unobserved path to a white object while allowing most marking to remain concurrent.</span>
<!-- true-recall: {"v":1,"id":"beddf753-23a0-4245-ab94-421da190d66d","schedules":[{"updatedAt":1793591126552,"due":"2026-11-02T03:46:26.532Z","stability":0.45140292,"difficulty":8.37863212,"reps":2,"lapses":0,"state":1,"lastReview":"2026-11-02T03:45:26.532Z","scheduledDays":0,"learningStep":0,"suspended":false,"createdAt":1793588719659}],"bases":{"dagoj9f7":{"front":"18d7a34143bde491bdf549dcfda3e1103e61cfa7e102ad6635721c05733580f7","back":"145f284a5f8fc43ba1c3e8d42a54310d8e261ed9f1d529f325b1abce3b81c1e6","reversed":false}}} -->

**What is mutator assist, and why can allocation slow down during a GC cycle?<span class="tr-accent-mint tr-tail-left"></span>**
<span class="tr-card-separator">??</span>
<span class="tr-card-answer">The mutator is application code that allocates and modifies memory. Go's pacer may require allocating goroutines to perform some marking work—mutator assist—when allocation outpaces the collector. This helps finish marking before the heap grows too far, trading some allocation latency for bounded memory growth.</span>
<!-- true-recall: {"v":1,"id":"5b90ed1d-11f4-4e01-8ef0-3ab69fac4b7c","schedules":[{"updatedAt":1793588719660,"due":"2026-11-02T03:05:19.660Z","stability":0,"difficulty":0,"reps":0,"lapses":0,"state":0,"lastReview":null,"scheduledDays":0,"learningStep":0,"suspended":false,"createdAt":1793588719660}],"bases":{"dagoj9f7":{"front":"c8649c299affa499a4976ee67b3b44e5aa11a6dca9beb5440f55ec1be14d4161","back":"1ee401728e994ca73cf399f9ec40bbce02460a28656322c5110aa82187d75d5d","reversed":false}}} -->

## Concurrency

**What is a goroutine?<span class="tr-accent-purple tr-tail-left"></span>**
<span class="tr-card-separator">??</span>
<span class="tr-card-answer">A lightweight concurrent function started with the `go` keyword.</span>
<!-- true-recall: {"v":1,"id":"267e9375-6647-49ab-b4ad-bf122f04e3b9","schedules":[{"updatedAt":1793588137909,"due":"2026-11-10T02:55:37.892Z","stability":8.2956,"difficulty":1,"reps":1,"lapses":0,"state":2,"lastReview":"2026-11-02T02:55:37.892Z","scheduledDays":8,"learningStep":0,"suspended":false,"createdAt":1793523989275}],"bases":{"dagoj9f7":{"front":"2f2d428e5ed20b49d8881591273466885c6992ccc65887dcc4c5550bcc55aa38","back":"e434a8e1723cd4bf7337a6a85a9b4f7b16ed9971bbb65f4de0e9ffa09d1112b6","reversed":false}}} -->

**What is a channel?<span class="tr-accent-mint tr-tail-right"></span>**
<span class="tr-card-separator">??</span>
<span class="tr-card-answer">A typed mechanism for communicating values between goroutines.</span>
<!-- true-recall: {"v":1,"id":"9c88d3c1-cb52-4596-a044-257fdb17580a","schedules":[{"updatedAt":1793587778191,"due":"2026-11-12T02:49:38.163Z","stability":8.2956,"difficulty":1,"reps":1,"lapses":0,"state":2,"lastReview":"2026-11-02T02:49:38.163Z","scheduledDays":10,"learningStep":0,"suspended":false,"createdAt":1793523989276}],"bases":{"dagoj9f7":{"front":"7feebb07a33590a577dbef954a632b1c6db2b153121ba7acf7a99817ca0b5c62","back":"00c7befb9929ed68e118756d4779b81a236f724b8fe7ef2d7d0f739eb6f35b19","reversed":false}}} -->

**How do buffered and unbuffered channels differ?<span class="tr-accent-amber tr-tail-left"></span>**
<span class="tr-card-separator">??</span>
<span class="tr-card-answer">`An unbuffered send` waits for a receiver; a buffered channel can hold values up to its capacity before a send blocks. One has queue while other ones do not have it.</span>
<!-- true-recall: {"v":1,"id":"bb8862ee-79fc-4b91-b88d-2a66cadf47ee","schedules":[{"updatedAt":1793588158632,"due":"2026-11-08T02:55:58.615Z","stability":8.2956,"difficulty":1,"reps":1,"lapses":0,"state":2,"lastReview":"2026-11-02T02:55:58.615Z","scheduledDays":6,"learningStep":0,"suspended":false,"createdAt":1793523989278}],"bases":{"dagoj9f7":{"front":"3eb1bdb58c20a4855650a1a8c4f3c0badd31a3fcefeb3517fa5e405de42b97b1","back":"c8be1a26876ed24ab03d3477a9a8817e5f5074c68be4a8df5ae75735e7079792","reversed":false}}} -->

**What is `select` used for?<span class="tr-accent-teal tr-tail-right"></span>**
<span class="tr-card-separator">??</span>
<span class="tr-card-answer">It waits until one of several channel operations can proceed.</span>
<!-- true-recall: {"v":1,"id":"202f644b-4cc0-41c3-9896-4ee37e5946c4","schedules":[{"updatedAt":1793588085667,"due":"2026-11-09T02:54:45.648Z","stability":8.2956,"difficulty":1,"reps":1,"lapses":0,"state":2,"lastReview":"2026-11-02T02:54:45.648Z","scheduledDays":7,"learningStep":0,"suspended":false,"createdAt":1793523989279}],"bases":{"dagoj9f7":{"front":"fa4f1fe39a8ca0eb76f3f559d149330224ad3e7cf1226771d7b9adfa7180a528","back":"f70e51b8cede0336dc6b8adc7b0128f1a31c2a977461ae0eb1e2efd4c09f7f40","reversed":false}}} -->

**How can you detect data races while testing Go code?<span class="tr-accent-blue tr-tail-left"></span>**
<span class="tr-card-separator">??</span>
<span class="tr-card-answer">Run `go test -race ./...`.</span>
<!-- true-recall: {"v":1,"id":"66ffffd9-561c-43ba-ac76-84a51160aeaa","schedules":[{"updatedAt":1793588177821,"due":"2026-11-11T02:56:17.801Z","stability":8.2956,"difficulty":1,"reps":1,"lapses":0,"state":2,"lastReview":"2026-11-02T02:56:17.801Z","scheduledDays":9,"learningStep":0,"suspended":false,"createdAt":1793523989280}],"bases":{"dagoj9f7":{"front":"8c92b1715bcfb42c1a37d4534b7c5e45bbeba11e93e0b9661dbe45bb7236c21f","back":"e2f1b810f912392a67a4a481737e70c99974ba5b7573ee8c6d908c670a3a8a1b","reversed":false}}} -->

**What does “happens before” mean in Go's memory model?<span class="tr-accent-coral tr-tail-right"></span>**
<span class="tr-card-separator">??</span>
<span class="tr-card-answer">It is the ordering that guarantees one goroutine's writes are visible to another. For example, a channel send happens before the matching receive completes, an unlock happens before a later lock on the same mutex returns, and `WaitGroup.Done` happens before an unblocked `Wait` returns. Without such synchronization, concurrent access can be a data race and observed values are not reliable.</span>
<!-- true-recall: {"v":1,"id":"993a21ce-d893-4b10-85b4-8b2b4aa1f357","schedules":[{"updatedAt":1793588859281,"due":"2026-11-02T03:07:39.281Z","stability":0,"difficulty":0,"reps":0,"lapses":0,"state":0,"lastReview":null,"scheduledDays":0,"learningStep":0,"suspended":false,"createdAt":1793588859281}],"bases":{"dagoj9f7":{"front":"f21976a18678f141bafc9d3b5b03c4b536182e7123965707886d3c5ed413573b","back":"58e098ff98c1b2284acd830a57b2ed9edc004b63fa468e471156e8aed15adeae","reversed":false}}} -->

**What are the rules and effects of closing a channel?<span class="tr-accent-purple tr-tail-left"></span>**
<span class="tr-card-separator">??</span>
<span class="tr-card-answer">Only the sender side should close, and only when it can prove that no more sends will occur. Closing broadcasts that no further values will be sent: receives first drain buffered values, then return the element type's zero value with `ok == false`. Sending on a closed channel panics; closing it twice also panics.</span>
<!-- true-recall: {"v":1,"id":"cd715519-924a-4759-a5ce-ddb83db1bddf","schedules":[{"updatedAt":1793588859282,"due":"2026-11-02T03:07:39.282Z","stability":0,"difficulty":0,"reps":0,"lapses":0,"state":0,"lastReview":null,"scheduledDays":0,"learningStep":0,"suspended":false,"createdAt":1793588859282}],"bases":{"dagoj9f7":{"front":"2e17420833dff8ea75121f20b1ded467b764ccc1fb4f567b24971df22c9c7ca9","back":"225cd77b1eba7025c9940aee0b1eaf1794b3722c558f9d64e18087c989fbc52e","reversed":false}}} -->

**How do nil channels behave, and when are they useful in `select`?<span class="tr-accent-mint tr-tail-right"></span>**
<span class="tr-card-separator">??</span>
<span class="tr-card-answer">A send to or receive from a nil channel blocks forever; closing a nil channel panics. In a `select`, a case with a nil channel is disabled. Setting a channel variable to nil is therefore a useful way to turn off a case dynamically, for example after that input has been closed and drained.</span>
<!-- true-recall: {"v":1,"id":"502d779a-2343-4629-8518-86bd789daab8","schedules":[{"updatedAt":1793588859283,"due":"2026-11-02T03:07:39.283Z","stability":0,"difficulty":0,"reps":0,"lapses":0,"state":0,"lastReview":null,"scheduledDays":0,"learningStep":0,"suspended":false,"createdAt":1793588859283}],"bases":{"dagoj9f7":{"front":"cbf7d503a6d8bdf29dc2b169ed5ea2bf97f021d5f0acba14337452bf4bb52cc1","back":"47ee4b9ac9918f543e861ba31d7dce75c6bd13518f2a912f89ce30f4cd075364","reversed":false}}} -->

**Does `select` guarantee fairness among ready cases?<span class="tr-accent-amber tr-tail-left"></span>**
<span class="tr-card-separator">??</span>
<span class="tr-card-answer">No fairness guarantee should be relied on. When multiple cases can proceed, the runtime chooses pseudo-randomly among them. This avoids a fixed priority in ordinary use but does not prove that every ready case will eventually run; design protocols so correctness does not depend on fairness. It does not like Java (prioritize the longest wait thread)</span>
<!-- true-recall: {"v":1,"id":"d0147ccc-5ba8-40a8-ab4c-7d2316c5de7c","schedules":[{"updatedAt":1793591881641,"due":"2026-11-02T04:08:01.622Z","stability":2.3065,"difficulty":2.11810397,"reps":1,"lapses":0,"state":1,"lastReview":"2026-11-02T03:58:01.622Z","scheduledDays":0,"learningStep":1,"suspended":false,"createdAt":1793588859283}],"bases":{"dagoj9f7":{"front":"13eb407b249dc6a9589345c3b1f6c034bad3bd362d03502a3cf25f8c05e8743c","back":"e1a5d1522b290b6001dc591ab484c066ee84bae692f20108fd34952c5fbb58d6","reversed":false}}} -->

**Why must `WaitGroup.Add` normally occur before starting the goroutine it counts?<span class="tr-accent-teal tr-tail-right"></span>**
<span class="tr-card-separator">??</span>
<span class="tr-card-answer">If a goroutine can call `Done` before its corresponding `Add`, the counter may become negative and panic, or `Wait` may return before the work was registered. Establish the count before launching work: `wg.Add(1); go func() { defer wg.Done(); work() }()`. A `WaitGroup` coordinates completion; it does not protect shared data.</span>
<!-- true-recall: {"v":1,"id":"a2e9ff09-f736-4e50-8c67-0b1f91cb04e9","schedules":[{"updatedAt":1793588859285,"due":"2026-11-02T03:07:39.285Z","stability":0,"difficulty":0,"reps":0,"lapses":0,"state":0,"lastReview":null,"scheduledDays":0,"learningStep":0,"suspended":false,"createdAt":1793588859285}],"bases":{"dagoj9f7":{"front":"dae2ca33226e95318d302498f6b2c77e7e56e23f93289188766910fb989b81a7","back":"31320f8b72f74e039c6df25a71aaa6299c1b5f930f6745b20a4163621a35d6b6","reversed":false}}} -->

**Why does calling `cancel()` on a context not stop a goroutine by itself?<span class="tr-accent-blue tr-tail-left"></span>**
<span class="tr-card-separator">??</span>
<span class="tr-card-answer">Cancellation closes `ctx.Done()` and records an error; it is cooperative, not a forced termination mechanism. The goroutine and every blocking operation it invokes must select on `ctx.Done()` or use a context-aware API. Also call the returned cancel function to release timers and cancellation resources when the work finishes early.</span>
<!-- true-recall: {"v":1,"id":"edf14ad7-2a4f-4abc-abcf-ae0c62725ca2","schedules":[{"updatedAt":1793588859286,"due":"2026-11-02T03:07:39.286Z","stability":0,"difficulty":0,"reps":0,"lapses":0,"state":0,"lastReview":null,"scheduledDays":0,"learningStep":0,"suspended":false,"createdAt":1793588859286}],"bases":{"dagoj9f7":{"front":"170d273d66a81096e6cd1b716c82fb44a131d9364817076c66558711d215a6d5","back":"0750fab71defbfe6e27a7e96f56d51bff6f6ecd9c8c4924760bf88f42f9112a5","reversed":false}}} -->

**When should you use a mutex instead of a channel to protect shared state?<span class="tr-accent-coral tr-tail-right"></span>**
<span class="tr-card-separator">??</span>
<span class="tr-card-answer">Use a mutex when goroutines directly share mutable state and the critical section is small and clear. Use channels primarily to transfer ownership, sequence work, or apply backpressure. Either can be correct; forcing simple state protection through channels often obscures ownership, while sharing mutable state through a channel without a protocol still races.</span>
<!-- true-recall: {"v":1,"id":"09b65342-cc58-4b8b-932f-e448e6b5af99","schedules":[{"updatedAt":1793588859287,"due":"2026-11-02T03:07:39.287Z","stability":0,"difficulty":0,"reps":0,"lapses":0,"state":0,"lastReview":null,"scheduledDays":0,"learningStep":0,"suspended":false,"createdAt":1793588859287}],"bases":{"dagoj9f7":{"front":"3cc7ae3c74e1aba3e8803fa19dc436a71199f92b2f234a8ac22e2358861fd35f","back":"01e6e2da2377cd1ac53f735a8e27777d0541d0501fb43b00d045ce88a549b382","reversed":false}}} -->

**Why is copying a value that contains a `sync.Mutex` or `sync.Once` dangerous after first use?<span class="tr-accent-purple tr-tail-left"></span>**
<span class="tr-card-separator">??</span>
<span class="tr-card-answer">**These synchronization values contain internal state**. A copy creates a distinct lock or once-state while the protected data may still be shared, breaking the intended coordination and potentially deadlocking or racing. Store them as fields, use pointer receivers for types that contain them, and avoid copying such values after first use.</span>
<!-- true-recall: {"v":1,"id":"a38a6201-6598-4931-8f7e-8259200bbf76","schedules":[{"updatedAt":1793591145837,"due":"2026-11-05T03:45:45.816Z","stability":3.94605407,"difficulty":1,"reps":2,"lapses":0,"state":2,"lastReview":"2026-11-02T03:45:45.816Z","scheduledDays":3,"learningStep":0,"suspended":false,"createdAt":1793588859288}],"bases":{"dagoj9f7":{"front":"b1783ed65b1019902bc86e69845dc6314223bd7d22ad9c2b1a5f6354a38c6575","back":"0ab944306e100f300fa0724daccec0236500907f49c92716663dfe7e46f7a3de","reversed":false}}} -->

**How can a pipeline (data model over multiple stages) avoid leaking goroutines when a downstream consumer stops early?<span class="tr-accent-mint tr-tail-left"></span>**
<span class="tr-card-separator">??</span>
<span class="tr-card-answer">Every stage must have a cancellation path. Pass a context or a done channel through the pipeline, and make sends select between the output channel and cancellation. The consumer cancels on error or early success; producers observe cancellation, stop their loops, and close only the channels they own.</span>
<!-- true-recall: {"v":1,"id":"39cdfb02-33c0-4151-8c60-5efa20ef9c47","schedules":[{"updatedAt":1793591556169,"due":"2026-11-04T03:52:36.153Z","stability":2.3065,"difficulty":2.11121424,"reps":2,"lapses":0,"state":2,"lastReview":"2026-11-02T03:52:36.153Z","scheduledDays":2,"learningStep":0,"suspended":false,"createdAt":1793588863919}],"bases":{"dagoj9f7":{"front":"b95fc2f41ce9d439ed1f99d9944dc5beb33c4acddc162a6df4134195ae4095cc","back":"50ca59a1005e50e5b59c41065371655a573a119a3002c1aa0fd9c6327f073b0f","reversed":false}}} -->

## Tooling and practices
**What is `context.Context` used for?<span class="tr-accent-coral tr-tail-right"></span>**
<span class="tr-card-separator">??</span>
<span class="tr-card-answer">To propagate cancellation, deadlines, and request-scoped values across API boundaries.</span>
<!-- true-recall: {"v":1,"id":"909ee428-55df-4f91-9040-155e036a92cd","schedules":[{"updatedAt":1793587802282,"due":"2026-11-12T02:50:02.259Z","stability":8.2956,"difficulty":1,"reps":1,"lapses":0,"state":2,"lastReview":"2026-11-02T02:50:02.259Z","scheduledDays":10,"learningStep":0,"suspended":false,"createdAt":1793523989281}],"bases":{"dagoj9f7":{"front":"06539d4c7d0939a6b11a84a7984daa6c0b20b192b1afc5935fa672c6e9aa0270","back":"a19e8534fd96adf82f5a30a62e1a532cdba351a36d5685578787716390645f62","reversed":false}}} -->

**How do you run all tests in a Go module?<span class="tr-accent-mint tr-tail-left"></span>**
<span class="tr-card-separator">??</span>
<span class="tr-card-answer">Run `go test ./...`.</span>
<!-- true-recall: {"v":1,"id":"347336a7-760e-432b-80f7-a3dd9b6a975a","schedules":[{"updatedAt":1793588173224,"due":"2026-11-10T02:56:13.207Z","stability":8.2956,"difficulty":1,"reps":1,"lapses":0,"state":2,"lastReview":"2026-11-02T02:56:13.207Z","scheduledDays":8,"learningStep":0,"suspended":false,"createdAt":1793523989282}],"bases":{"dagoj9f7":{"front":"fd93cc6d8c4f0e3d2de0af49e5867d7f81b0bed1d12b28ee09418a8e50d38e76","back":"e4a085aaa0e53bda03854342fc196d3dbb61d4ef98254d0b479f4997b2678029","reversed":false}}} -->

**What does `go mod tidy` do?<span class="tr-accent-purple tr-tail-right"></span>**
<span class="tr-card-separator">??</span>
<span class="tr-card-answer">It adds missing module requirements and removes module dependencies that are no longer needed.</span>
<!-- true-recall: {"v":1,"id":"baedae18-89cf-4288-8c8c-58057b8d6866","schedules":[{"updatedAt":1793588184199,"due":"2026-11-12T02:56:24.181Z","stability":8.2956,"difficulty":1,"reps":1,"lapses":0,"state":2,"lastReview":"2026-11-02T02:56:24.181Z","scheduledDays":10,"learningStep":0,"suspended":false,"createdAt":1793523989285}],"bases":{"dagoj9f7":{"front":"6cfff992561cc003390a90066355bf0efd7a055f3e09ec9ffee1676278d95b7a","back":"8238d68cd34f8a213423d6a7afe30ee771e34243b9c7c6e83bbbc8a641a2b5a8","reversed":false}}} -->

**Why should Go source files be formatted with `gofmt`?<span class="tr-accent-amber tr-tail-left"></span>**
<span class="tr-card-separator">??</span>
<span class="tr-card-answer">It applies Go's standard formatting rules, keeping code consistent and easy to review.</span>
<!-- true-recall: {"v":1,"id":"6e198a85-29c9-4747-a7e4-d58608bfa2c1","schedules":[{"updatedAt":1793587771025,"due":"2026-11-08T02:49:31.008Z","stability":8.2956,"difficulty":1,"reps":1,"lapses":0,"state":2,"lastReview":"2026-11-02T02:49:31.008Z","scheduledDays":6,"learningStep":0,"suspended":false,"createdAt":1793523989286}],"bases":{"dagoj9f7":{"front":"00df81ed492776cbba05d9fb35dcd9f5acd08672578d4721c7a8fa2c80e3ea59","back":"321e21795fc29854c882ddd9e5ca87f6688550e64a796d74a9e39712d46c7dfd","reversed":false}}} -->
