# Gemini AI Helpers

A collection of Gemini CLI extensions to automate and assist with various development tasks.

## Installation

### Install the entire collection

Run the following command inside your Gemini CLI session:

```
gemini extensions install https://github.com/wangke19/gemini-ai-helpers
```

Or using SSH:

```
gemini extensions install git@github.com:wangke19/gemini-ai-helpers
```

### Use the commands

```
/jira:solve OCPBUGS-12345 origin
```

## Updating Extensions

To get the latest extension versions:

```
gemini extensions update gemini-ai-helpers
```

## Available Extensions

| Extension | Description |
|-----------|-------------|
| `agendas` | Meeting agenda management and preparation |
| `bigquery` | BigQuery data analysis and query assistance |
| `ci` | CI/CD pipeline management and debugging |
| `code-review` | Automated code review workflows |
| `compliance` | Compliance checking and validation |
| `container-image` | Container image build and management |
| `doc` | Documentation generation and maintenance |
| `etcd` | etcd cluster diagnostics and management |
| `git` | Git workflow helpers and automation |
| `golang` | Go development utilities and helpers |
| `gwapi` | Gateway API management and configuration |
| `hcp` | HyperShift/HCP cluster management |
| `hello-world` | Reference implementation and examples |
| `jira` | Jira issue management and automation |
| `lvms` | LVMS (Logical Volume Manager Storage) analysis |
| `macos-notifications` | macOS system notifications for session events |
| `metrics` | Metrics collection and reporting |
| `must-gather` | OpenShift must-gather diagnostic analysis |
| `node` | Node health checks and diagnostics |
| `node-tuning` | Node tuning profile analysis and generation |
| `olm` | OLM (Operator Lifecycle Manager) workflows |
| `olm-team` | OLM team-specific tooling and agents |
| `openshift` | OpenShift development utilities |
| `origin` | OpenShift origin (two-node) PR helpers |
| `ote-migration` | OTE migration workflow assistance |
| `session` | Session management and persistence |
| `sosreport` | SOS report analysis and diagnostics |
| `teams` | Team health checks, regression analysis |
| `test-coverage` | Test coverage analysis and gap detection |
| `testing` | Mutation testing and test generation |
| `utils` | General-purpose utilities and helpers |
| `workspaces` | Multi-repo workspace management |
| `yaml` | YAML documentation and utilities |

## Extension Development

Want to contribute or create your own extensions? Check out the `extensions/` directory for examples.
Make sure your commands and agents follow the conventions for the Sections structure presented in the hello-world reference implementation extension (see [`hello-world:echo`](extensions/hello-world/commands/echo.md) for an example).

### Ethical Guidelines

Extensions, commands, skills, and hooks must NEVER reference real people by name, even as stylistic examples (e.g., "in the style of <specific human>").

**Ethical rationale:**
1. **Consent**: Individuals have not consented to have their identity or persona used in AI-generated content
2. **Misrepresentation**: AI cannot accurately replicate a person's unique voice, style, or intent
3. **Intellectual Property**: A person's distinctive style may be protected
4. **Dignity**: Using someone's identity without permission diminishes their autonomy

**Instead, describe specific qualities explicitly**

Good examples:

* "Write commit messages that are direct, technically precise, and focused on the rationale behind changes"
* "Explain using clear analogies, a sense of wonder, and accessible language for non-experts"
* "Code review comments that are encouraging, constructive, and focus on collaborative improvement"

When you identify a desirable characteristic (clarity, brevity, formality, humor, etc.), describe it explicitly rather than using a person as proxy.

### Adding New Commands

**Check for overlaps first** - Before coding, validate your idea:

```bash
/utils:review-ai-helpers-overlap --idea "brief description of your command"
```

Collaborating on existing work instead of duplicating parallel efforts is always encouraged when overlap is found. This helps maintain a clean, non-redundant extension collection in such an actively developed project.

When contributing new commands:

1. **If your command fits an existing extension**: Add it to the appropriate extension's `commands/` directory
2. **If your command doesn't have a clear parent extension**: Add it to the **utils extension** (`extensions/utils/commands/`)
   - The utils extension serves as a catch-all for commands that don't fit existing categories
   - Once we accumulate several related commands in utils, they can be segregated into a new targeted extension

### Creating a New Extension

If you're contributing several related commands that warrant their own extension:

1. Create a new directory under `extensions/` with your extension name
2. Create the extension structure:
   ```
   extensions/your-extension/
   ├── .gemini-extension/
   │   └── extension.json
   └── commands/
       └── your-command.md
   ```
3. Register your extension in `.gemini-extension/marketplace.json`

## Additional Documentation

- **[LICENSE](LICENSE)** - License details

## License

See [LICENSE](LICENSE) for details.
