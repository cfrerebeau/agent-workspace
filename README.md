# Agent Workspace

A containerized, sandboxed environment for running AI agents on creative and document tasks—without touching your production code.

**Fork this repo, make it private, and you have a secure backup of all your thinking, notes, and AI-assisted work.**

---

## What Is This?

Agent Workspace is an open-source starter kit designed for people who want to:

- Run AI agents in a safe, reproducible container environment
- Work on **creative writing**, **document editing**, and **brainstorming**—not just coding
- Track exactly what the AI modified using Git version control
- Keep a private backup of their work and thinking process

This project comes pre-configured with:

- **Claude Code** - Anthropic's CLI for working with Claude AI
- **BMAD Framework** - Reusable agents for creative tasks (brainstorming, storytelling, design thinking)
- **Document Skills** - Edit Excel, Word, PowerPoint, and PDF files directly
- **Office Document Viewer** - VSCode extension to preview documents

---

## Quick Start: Two Ways to Run

### Option 1: Run in the Cloud (GitHub Codespaces)

**No installation required.** GitHub Codespaces runs the container in the cloud.

1. **Fork this repository**
   - Click the **Fork** button at the top right of this page
   - Recommended: Make your fork **private** to keep your work secure

2. **Open in Codespaces**
   - Go to your forked repository
   - Click the green **Code** button
   - Select the **Codespaces** tab
   - Click **Create codespace on main**

3. **Wait for setup** (2-3 minutes first time)
   - The container will build and install all dependencies
   - VSCode opens in your browser when ready

4. **Add your API key**
   - You need a Claude API key or Max subscription
   - Run: `claude` in the terminal to start and configure

**Codespaces Pricing:** Free tier includes 60 hours/month. See [GitHub Codespaces pricing](https://github.com/features/codespaces).

---

### Option 2: Run Locally (Your Computer)

Run the container on your own machine for unlimited usage.

#### Minimum Requirements

| Component | Minimum | Recommended |
|-----------|---------|-------------|
| RAM | 8 GB | 16 GB |
| Storage | 10 GB free | 20 GB free |
| CPU | 4 cores | 8 cores |
| OS | Windows 10/11, macOS 10.15+, Linux | Any modern OS |

#### Step 1: Install Required Software

1. **Install Rancher Desktop** (container runtime)
   - Download: [https://rancherdesktop.io/](https://rancherdesktop.io/)
   - During setup, select **dockerd (moby)** as the container engine
   - This replaces Docker Desktop with a free, open-source alternative

2. **Install Visual Studio Code**
   - Download: [https://code.visualstudio.com/](https://code.visualstudio.com/)
   - Install the **Dev Containers** extension:
     - Open VSCode
     - Press `Ctrl+Shift+X` (or `Cmd+Shift+X` on Mac)
     - Search for "Dev Containers"
     - Install the extension by Microsoft

#### Step 2: Clone and Open the Repository

1. **Fork this repository** on GitHub (make it private if desired)

2. **Clone your fork:**
   ```bash
   git clone https://github.com/YOUR-USERNAME/agent-workspace.git
   cd agent-workspace
   ```

3. **Open in VSCode:**
   ```bash
   code .
   ```

4. **Reopen in Container:**
   - VSCode will detect the dev container configuration
   - Click **Reopen in Container** when prompted
   - Or press `F1`, type "Reopen in Container", and select it

5. **Wait for build** (5-10 minutes first time)

6. **Add your API key:**
   - Run `claude` in the terminal to configure

---

## Working with AI Agents

### Starting Claude

Open a terminal in VSCode and run:

```bash
claude
```

This starts Claude Code, an interactive AI assistant that can:
- Edit files directly in your workspace
- Run commands and scripts
- Work with documents (Excel, Word, PDF, PowerPoint)
- Use BMAD agents for creative tasks

### Using BMAD Agents

BMAD provides specialized agents for creative work. Start with:

```
/bmad:core:agents:bmad-master
```

This launches the BMad Master, who can help you:
- **Brainstorm ideas** with structured techniques
- **Write stories** with the Storyteller agent
- **Solve problems** with the Creative Problem Solver
- **Design with empathy** using the Design Thinking Coach

See the [BMAD Project](https://github.com/bmadcode/BMAD-METHOD) for full documentation.

---

## Git Basics: Tracking What the Agent Changed

One of the biggest benefits of this setup: **you can see exactly what the AI modified**.

### Essential Commands

```bash
# See what files changed
git status

# See the actual changes (line by line)
git diff

# Save your changes with a message
git commit -am "Added brainstorming notes for project X"

# Push to your private backup (GitHub)
git push
```

### Recommended Workflow

1. **Before starting a task:** Check `git status` to see your current state
2. **After AI edits files:** Run `git diff` to review what changed
3. **When satisfied:** Commit with a descriptive message
4. **Periodically:** Push to GitHub as your backup

### Why This Matters

- **Accountability:** See every line the AI added, changed, or removed
- **Undo mistakes:** Revert any change with `git checkout -- filename`
- **History:** Browse your entire thinking process over time
- **Backup:** Your private GitHub fork stores everything safely

---

## The `local` Folder: Private, Never Committed

The `/local` folder is special:

- It's listed in `.gitignore`
- **Nothing in this folder will ever be committed to Git**
- Perfect for sensitive notes, API keys, personal drafts

Use it for:
- Private brainstorming you don't want in version history
- Temporary files and experiments
- Sensitive information that shouldn't be backed up

---

## Extending This Workspace

### Adding Other LLM Providers

This workspace comes with Claude, but you can add other providers:

- Install additional CLI tools in the Dockerfile
- Configure API keys in the `/local` folder
- Modify `.devcontainer/devcontainer.json` to add features

### Building Your Own Agents

BMAD is a framework for creating reusable AI agents. You can:

1. Study the existing agents in `.bmad/`
2. Create your own agents for specific tasks
3. Build workflows that chain multiple agents together

See the [BMAD Builder documentation](.bmad/bmb/README.md) for guidance.

---

## Project Structure

```
agent-workspace/
├── .devcontainer/       # Container configuration
├── .bmad/               # BMAD agents and workflows
│   ├── core/            # Core agents (BMad Master)
│   ├── cis/             # Creative & Innovation Suite agents
│   └── bmb/             # BMad Builder (create your own agents)
├── .claude/             # Claude Code configuration and skills
├── local/               # Private folder (never committed)
├── docs/                # Output folder for generated documents
└── README.md            # You are here
```

---

## Troubleshooting

### Container won't start
- Ensure Rancher Desktop is running
- Try restarting Rancher Desktop
- Check you have enough disk space

### Claude command not found
- Wait for the container to fully build
- Try reopening the terminal
- Check the postCreateCommand completed successfully

### Can't push to GitHub
- Ensure you've forked (not just cloned) the original repo
- Check you have write access to your fork
- Configure Git credentials: `git config --global user.email "you@example.com"`

---

## License

This project is open source. Fork it, modify it, make it yours.

---

## Links

- [GitHub Codespaces Documentation](https://docs.github.com/en/codespaces)
- [Rancher Desktop](https://rancherdesktop.io/)
- [Visual Studio Code](https://code.visualstudio.com/)
- [Dev Containers Extension](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers)
- [BMAD Framework](https://github.com/bmadcode/BMAD-METHOD)
- [Claude Code Documentation](https://docs.anthropic.com/en/docs/claude-code)
