---
created: 2026-03-18T23:16:29+08:00
modified: 2026-03-18T23:16:41+08:00
---

# computer control agents

I've looked into your request for open-source agents that can control your computer (both terminal and GUI) and Android devices. Based on your initial ideas and my search, here's a breakdown of the most relevant projects.

For a quick overview, here are the projects that best match your criteria:

| Project Name | Desktop GUI Control | Terminal Operation | Android Control | Open Source License | Notes |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **Open-AutoGLM** | ❌ | ❌ | ✅ | MIT / Apache 2.0 | Phone-use agent from Zhipu; supports 50+ Chinese apps, runs on cloud or local. |
| **Cua** | ✅ | ✅ | ❌ | MIT | Docker-style container for running agents in isolated VMs (macOS/Linux). |
| **OpenClaw** | ✅ | ✅ | ❌ | Open Source (Implied) | Community-driven, uses Claude API for cross-platform computer use (macOS, Linux, Windows). |
| **GLM-PC (CogAgent-9B)** | ✅ | ✅ | ❌ | Open Source | Base model (CogAgent) is open-source for building GUI agents. |
| **DroidRun** | ❌ | ❌ | ✅ | MIT | Python framework for controlling Android with natural language via ADB. |
| **Toad** | ❌ | ✅ | ❌ | Proprietary (Preview) | Terminal UI for coding agents, currently in paid preview. |
| **simple-agent-go** | ❌ | ✅ | ❌ | MIT | Go framework for terminal-based AI agents with built-in bash and file tools. |

### 💡 How to Choose the Right Tool for You

With several strong options available, your choice will depend on your primary focus:
*   **If your main goal is Android phone control**: **Open-AutoGLM** or **DroidRun** are your best bets. Open-AutoGLM is a more complete, production-ready framework, while DroidRun offers a flexible Python-based approach.
*   **If you need to automate desktop applications in a secure, isolated environment**: **Cua** is an excellent choice. Its VM-based approach keeps your host system safe.
*   **If you want to build a custom agent that can control any desktop OS (macOS, Windows, Linux)**: **OpenClaw** provides the open-source blueprint to do this using Anthropic's powerful Claude models.
*   **If your focus is on a developer-centric tool for the terminal**: **simple-agent-go** offers a robust framework with built-in tools for file and command-line operations.

### 🤔 What's Next?

To help you narrow it down even further, a couple of quick questions:
*   What's your primary development language or framework (e.g., Python, Node.js, Go)?
*   What's the main task you're hoping to automate first (e.g., a repetitive Android task, a desktop workflow, or a coding process)?
