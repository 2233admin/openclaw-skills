# Tag Taxonomy

Complete reference for tag categories used in the knowledge base.

## area/ (Domain Categories)

### Integration & External Services
- `area/integration` - Third-party service integrations
- `area/telegram` - Telegram bot and features
- `area/memory` - Knowledge management and memory systems

### Development
- `area/skills` - OpenClaw skills development
- `area/openclaw` - OpenClaw core platform
- `area/model-serving` - LLM model hosting and serving
- `area/debugging` - Troubleshooting and debugging

### Workflow & Process
- `area/workflow` - Automation and workflow design
- `area/agent-persona` - Agent personality/character design
- `area/development-workflow` - Dev process improvements

### Other
- `area/analytics` - Data analysis and metrics
- `area/architecture` - System design and architecture
- `area/competitor-analysis` - Competitive research
- `area/config` - Configuration management
- `area/core` - Core platform features
- `area/llm` - LLM-related topics
- `area/meta-programming` - Meta-level programming
- `area/philosophy` - Design philosophy
- `area/prompt-engineering` - Prompt design
- `area/ui` - User interface

## type/ (Task Types)

- `type/research` - Investigation and analysis
- `type/implementation` - Building and implementing
- `type/creation` - Creating new agents/skills
- `type/done` - Completed tasks
- `type/automation` - Automation scripts
- `type/refactor` - Refactoring existing code
- `type/clarification` - Clarifying ambiguities
- `type/bug-hunt` - Debugging specific issues

## service/ (Specific Services)

- `service/gemini-local` - Gemini Local model service

## Usage patterns

### Single category
```yaml
tags:
  - area/integration
```

### Multiple categories
```yaml
tags:
  - area/integration
  - type/implementation
```

### With service
```yaml
tags:
  - area/model-serving
  - service/gemini-local
  - bug
```
