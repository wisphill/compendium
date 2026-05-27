POM: generated page object models for a webpage
Cucumber test steps: 
Gherkin .feature files:
Hooks: Inject scripts to trigger customized function like (snapshotting before erroring)
World: shared space for contexts

JIRA tiket -> Gherkin .features
MCP server + Gherkin .features -> Generate POM files 


### OpenAI CLI session  
1. base context: Decide to generate Gherkins, or generate POM files.
2. loader 1: (load MCP commands, Jira MCP commands)
3. Base on the context, LLM will decide which MCP tools to call, after the cli call MCP tools > trigger LLM call to let it know > Now, load the ticket info/ more information to the context. For e.g, we have enough information to generate Gherkin.

### OpenAI CLI session for generating POM files & test steps
1. base context: Decide to generate POM files & test steps
2. loader 1: (load MCP commands: Playwright MCP commands (base MCP commands for navigation, DOM, snapshot, customized module commands))
3. loader 2: load Gherkin.feature for exploration + load customized prompts for the output formats, standards
4. loader 3: load secrets, vault key path.
5. Exploration: Base on the context, LLM will decide which MCP tools to call, after each call > ack to LLM > can limit numbers of self healing steps (???) > Generated POM & test steps.