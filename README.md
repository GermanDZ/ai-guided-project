# [PROJECT_NAME] (i.e.: "My new AI-guided project")

> One-line description of what this project does.

Brief paragraph explaining the project's purpose, who it's for, and what problem it solves.

---

## Getting Started

### Prerequisites

- Git
- [Claude Code](https://docs.anthropic.com/en/docs/claude-code) (recommended for AI-assisted development)
- Your language runtime (Node.js, Python, Ruby, Go, Rust, Java, etc.)

### Install Claude Code

```bash
# Using Homebrew (macOS/Linux)
brew install claude-code

# Or using npm (if Node.js is available)
npm install -g @anthropic-ai/claude-code
```

### Initialize the Project

```bash
# Clone the repository
git clone https://github.com/username/sample-02.git
cd sample-02

# Start Claude Code
claude
```

On first run, Claude will read `CLAUDE.md` and the workflow docs automatically.

### First Steps

After cloning, complete the setup tasks in `docs/how-to-work/roadmap.md`:

1. Define your tech stack in `docs/how-to-work/stack.md`
2. Document your architecture in `docs/how-to-work/architecture.md`
3. Set up your local environment (see [Local Development](#local-development))
4. Configure your deployment pipeline (see [Deployment](#deployment))

---

## Stack Compatibility

This template is **language and framework agnostic**. It works with any stack:

- **Languages**: TypeScript, JavaScript, Python, Ruby, Go, Rust, Java, C#, etc.
- **Frameworks**: React, Rails, Django, Spring, Gin, Actix, Express, etc.
- **Platforms**: Web, API, CLI, mobile, desktop, embedded

The workflow documentation (`docs/how-to-work/`) defines _how_ you work, not _what_ you build with. Code examples in templates are placeholders—replace them with your stack's equivalents.

---

## Local Development

_Document how to run the project locally._

```bash
# Install dependencies
# [Add your command here]

# Run the development server
# [Add your command here]

# The app will be available at http://localhost:[PORT]
```

See `docs/local-development.md` for detailed setup instructions.

---

## Running Tests

_Document how to run the test suite._

```bash
# Run all tests
# [Add your command here]

# Run tests in watch mode
# [Add your command here]

# Run tests with coverage
# [Add your command here]
```

See `docs/testing.md` for testing conventions and guidelines.

---

## Deployment

_Document how to deploy to production._

### Environments

| Environment | URL           | Branch    |
| ----------- | ------------- | --------- |
| Production  | _https://..._ | `main`    |
| Staging     | _https://..._ | `develop` |

### Deploy Process

```bash
# [Add your deployment commands here]
```

See `docs/deployment.md` for detailed deployment instructions.

---

## Documentation

| Document                                       | Description                         |
| ---------------------------------------------- | ----------------------------------- |
| [Local Development](docs/local-development.md) | How to set up and run locally       |
| [Testing](docs/testing.md)                     | Testing strategy and commands       |
| [Deployment](docs/deployment.md)               | Deployment process and environments |
| _Add more as needed_                           |                                     |

---

## Working with This Project

This project uses a documentation-driven workflow in `/docs/how-to-work`. These docs define how humans and AI agents collaborate to build software, following Agile principles.

### For Developers

Before contributing, read:

1. **[agent.md](docs/how-to-work/agent.md)** — The workflow philosophy and process
2. **[stack.md](docs/how-to-work/stack.md)** — Technology choices
3. **[architecture.md](docs/how-to-work/architecture.md)** — System design
4. **[conventions.md](docs/how-to-work/conventions.md)** — Coding standards

### For AI Agents (Claude Code)

Start every session by reading the docs in this order:

```
docs/how-to-work/agent.md → stack.md → architecture.md → conventions.md → roadmap.md
```

### Workflow Documents

| Document            | Type        | Purpose                               |
| ------------------- | ----------- | ------------------------------------- |
| `architecture.md`   | State       | Current system design                 |
| `stack.md`          | State       | Current tech choices                  |
| `conventions.md`    | State       | Coding standards                      |
| `roadmap.md`        | State       | Tasks and priorities                  |
| `glossary.md`       | State       | Domain terminology                    |
| `decisions.md`      | Incremental | Architectural decisions (append-only) |
| `changelog.md`      | Incremental | Release history (append-only)         |
| `retrospectives.md` | Incremental | Lessons learned (append-only)         |

**State docs** reflect current truth—update them to stay accurate.  
**Incremental docs** are append-only—never modify past entries.

---

## Contributing

1. Check `docs/how-to-work/roadmap.md` for available tasks
2. Create a branch: `feature/issue-{number}-{description}`
3. Make small, atomic commits (each must pass tests)
4. Submit a PR solving exactly one issue
5. Wait for review before merging

See [agent.md](docs/how-to-work/agent.md) for the full workflow.

---

## Project Structure

```
sample-02/
├── docs/
│   ├── how-to-work/          # Workflow documentation
│   │   ├── agent.md          # AI collaboration guide
│   │   ├── architecture.md   # System design
│   │   ├── changelog.md      # Release history
│   │   ├── conventions.md    # Coding standards
│   │   ├── decisions.md      # Architectural Decision Records (ADRs). Each decision is numbered and dated. Never modify past decisions—add new ones that supersede if needed.
│   │   ├── glossary.md       # Domain terms and their definitions.
│   │   ├── rationale.md      # Rationale for the project
│   │   ├── retrospectives.md # Post-milestone and periodic reflections.
│   │   ├── roadmap.md        # Tasks & priorities.
│   │   └── stack.md          # Tech choices.
│   ├── local-development.md  # How to set up and run locally.
│   ├── testing.md            # Testing strategy and commands.
│   └── deployment.md         # Deployment process and environments.
├── src/                      # Source code (structure depends on stack).
├── tests/                    # Test files.
├── CLAUDE.md                 # AI agent instructions (open standard)
├── AGENTS.md                 # Quick context for Claude Code, redirects to AGENTS.md.
├── LICENSE                   # License for the project.
└── README.md                 # This file.
```

---

## License

[Choose a license] - See [LICENSE](LICENSE) for details.

---

## Acknowledgments

- _Credit contributors, libraries, or inspirations_
