# Amplifier Marketplace: AI-Powered Development Capabilities

> _"Coordinated development capabilities for Claude Code"_

> [!CAUTION]
> This project is a research demonstrator. It is in early development and may change significantly. Using permissive AI tools in your repository requires careful attention to security considerations and careful human supervision, and even then things can still go wrong. Use it with caution, and at your own risk. See [Disclaimer](#disclaimer).

Amplifier Marketplace is a Claude Code plugin marketplace providing AI-powered development capabilities including core utilities, Document-Driven Development methodology, design intelligence, knowledge synthesis, and example recipes. Each plugin provides specialized agents, commands, and workflows that enhance Claude Code's development capabilities.

## 🚀 QuickStart

### Prerequisites

Claude Code must be installed and configured. See [Claude Code Documentation](https://docs.anthropic.com/claude/docs/claude-code) for setup instructions.

### Installation

Install the marketplace as a Claude Code plugin:

```bash
# Install from GitHub
claude plugins install https://github.com/bryonjacob/amplifier-marketplace.git

# Or clone and install locally for development
git clone https://github.com/bryonjacob/amplifier-marketplace.git
claude plugins install ./amplifier-marketplace
```

### Get Started

```bash
# Start Claude Code
claude
```

The marketplace installs 5 plugins with their capabilities:

**Core Plugin (`amp`)** - Installed automatically:
- 21 specialized agents (zen-architect, bug-hunter, security-guardian, etc.)
- 11 utility commands (/amp:commit, /amp:prime, etc.)
- Core development workflows

**DDD Plugin (`ddd`)** - Document-Driven Development:
```
/ddd:1-plan         # Design the feature
/ddd:2-docs         # Update all docs (iterate until approved)
/ddd:3-code-plan    # Plan code changes
/ddd:4-code         # Implement and test
/ddd:5-finish       # Clean up and finalize
```

**Design Plugin (`amp-design`)** - Design Intelligence:
```
/amp-design:designer    # Orchestrated design workflow
```
Plus 7 design specialist agents (art-director, component-designer, layout-architect, etc.)

**Knowledge Plugin (`amp-knowledge`)** - Knowledge Synthesis:
- 10 knowledge synthesis agents
- Multi-perspective analysis tools

**Recipes Plugin (`amp-recipes`)** - Example implementations as Skills

**Try it out:**
```
# Use Document-Driven Development
/ddd:0-help

# Create with design intelligence
/amp-design:designer create a button component with hover states

# Commit with standardized messages
/amp:commit
```

---

## 📖 Plugin Capabilities

### Available Plugins

The marketplace provides 5 specialized plugins:

#### 1. **amp** (Core Plugin)
Required dependency for all other plugins.

**21 Specialized Agents:**
- `zen-architect` - Code planning, architecture design, and review
- `modular-builder` - Module implementation from specifications
- `bug-hunter` - Systematic debugging
- `security-guardian` - Security reviews and audits
- `test-coverage` - Test analysis and suggestions
- `integration-specialist` - External service integration
- `performance-optimizer` - Performance analysis and optimization
- `api-contract-designer` - API design and documentation
- `database-architect` - Database design and optimization
- Plus 12 more specialized agents

**11 Utility Commands:**
- `/amp:commit` - Standardized git commits
- `/amp:prime` - Load complete context
- Plus 9 more utility commands

#### 2. **ddd** (Document-Driven Development)
6-phase development workflow with numbered slash commands.

**Commands:**
- `/ddd:0-help` - Workflow guide
- `/ddd:1-plan` - Design and planning
- `/ddd:2-docs` - Documentation retcon
- `/ddd:3-code-plan` - Implementation planning
- `/ddd:4-code` - Code implementation
- `/ddd:5-finish` - Cleanup and finalization
- `/ddd:status` - Show current progress
- `/ddd:prime` - Load DDD context

#### 3. **amp-design** (Design Intelligence)
7 design specialist agents with evidence-based frameworks.

**Command:**
- `/amp-design:designer` - Orchestrated design workflow

**7 Design Agents:**
- `art-director` - Visual direction and aesthetic strategy
- `component-designer` - Component design and creation
- `layout-architect` - Information architecture
- `animation-choreographer` - Motion design
- `responsive-strategist` - Device adaptation
- `voice-strategist` - UI copy voice & tone
- `design-system-architect` - Design system architecture

**Framework:**
- 9 aesthetic dimensions (style, motion, voice, space, color, typography, proportion, texture, body)
- 4 design layers (foundational, structural, behavioral, experiential)
- WCAG 2.1 compliance, color theory, animation principles

#### 4. **amp-knowledge** (Knowledge Synthesis)
Multi-perspective knowledge analysis and synthesis.

**10 Knowledge Agents:**
- `concept-extractor` - Extract concepts from documents
- `insight-synthesizer` - Discover breakthrough insights
- `knowledge-archaeologist` - Trace idea evolution
- `visualization-architect` - Create knowledge visualizations
- `pattern-emergence` - Detect emergent patterns
- Plus 5 more synthesis agents

#### 5. **amp-recipes** (Example Recipes)
Example implementations demonstrating development patterns, provided as Claude Code Skills.

---

## ✨ Using the Plugins

### Plugin Development Workflow

Each plugin provides capabilities you use directly in Claude Code:

### Example Usage Patterns

**Document-Driven Development:**
```
/ddd:1-plan         # Start new feature
/ddd:2-docs         # Update documentation
/ddd:4-code         # Implement changes
/ddd:5-finish       # Clean up
```

**Design Intelligence:**
```
/amp-design:designer create a responsive navigation component

# Or use specific agents
Use art-director to establish visual direction
Deploy component-designer for the card component
```

**Code Architecture:**
```
Use zen-architect to design the caching layer
Have bug-hunter investigate the login failures
Deploy security-guardian for API review
```

**Knowledge Synthesis:**
```
Use concept-extractor on these research papers
Deploy insight-synthesizer to find connections
Have visualization-architect create a knowledge graph
```

### Documentation

- **Plugin Manifests:** [.claude-plugin/](plugins/)
- **Design Framework:** [ai_context/design/](ai_context/design/)
- **DDD Methodology:** [docs/document_driven_development/](docs/document_driven_development/)
- **Philosophy:** [ai_context/IMPLEMENTATION_PHILOSOPHY.md](ai_context/IMPLEMENTATION_PHILOSOPHY.md)

### Development

For marketplace development:

```bash
# Clone repository
git clone https://github.com/bryonjacob/amplifier-marketplace.git
cd amplifier-marketplace

# Install dependencies (shared Python packages)
make install

# Run quality checks
make check

# Run tests
make test
```

---

## Disclaimer

> [!IMPORTANT] > **This is an experimental system. _We break things frequently_.**

- Not accepting contributions yet (but we plan to!)
- No stability guarantees
- Pin commits if you need consistency
- This is a learning resource, not production software
- **No support provided** - See [SUPPORT.md](SUPPORT.md)

## Contributing

> [!NOTE]
> This project is not currently accepting external contributions, but we're actively working toward opening this up. We value community input and look forward to collaborating in the future. For now, feel free to fork and experiment!

Most contributions require you to agree to a
Contributor License Agreement (CLA) declaring that you have the right to, and actually do, grant us
the rights to use your contribution. For details, visit [Contributor License Agreements](https://cla.opensource.microsoft.com).

When you submit a pull request, a CLA bot will automatically determine whether you need to provide
a CLA and decorate the PR appropriately (e.g., status check, comment). Simply follow the instructions
provided by the bot. You will only need to do this once across all repos using our CLA.

This project has adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/).
For more information see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) or
contact [opencode@microsoft.com](mailto:opencode@microsoft.com) with any additional questions or comments.

## Trademarks

This project may contain trademarks or logos for projects, products, or services. Authorized use of Microsoft
trademarks or logos is subject to and must follow
[Microsoft's Trademark & Brand Guidelines](https://www.microsoft.com/legal/intellectualproperty/trademarks/usage/general).
Use of Microsoft trademarks or logos in modified versions of this project must not cause confusion or imply Microsoft sponsorship.
Any use of third-party trademarks or logos are subject to those third-party's policies.
