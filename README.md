# Agent Skills

This repository contains a collection of custom skills designed to enhance your development workflow within VS Code using an AI Agent.

## Available Skills

### 1. Create Dart Backend Project
- **Description:** Quickly sets up a new Dart backend project for you using the `dart_frog` framework.

### 2. Create Flutter Workspaces Project
- **Description:** Sets up a new Flutter project with a workspace structure using `flutter_workspaces_cli`, perfect for managing large applications or monorepos.

### 3. Code Reviewer
- **Description:** Acts as an automated code reviewer, checking your recent code changes (`git diff`) and suggesting improvements based on principles like SOLID and Clean Code.

## VS Code Setup

To integrate these skills into your VS Code environment:

1.  **Clone Repository:**
    Clone this repository to your machine.
    ```bash
    git clone https://github.com/ThiagoEvoa/agent_skills.git
    ```

2.  **Create Skills folder**
    In the root of your project create this folder structure.
    ```
    project/
    ├── .agents/                    
    │   ├── skills/
    │   │   └── skill_folder        
   
    ```

3.  **User Settings (JSON):**
    Add this configuration to your User Settings (JSON)
    ```bash
    "chat.agentSkillsLocations": {
        "~/.agents/skills/": true
    }
    ```

4.  **Verify:**
    Open the AI Chat in VS Code and try a trigger phrase like:
    > "Review my code changes"

    If the agent recognizes the intent and executes the `code-reviewer` skill, the setup is complete.
