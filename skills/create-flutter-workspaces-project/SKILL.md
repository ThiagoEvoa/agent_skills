---
name: create-flutter-workspaces-project
description: Initializes a new Flutter with workspaces template project using the flutter_workspaces_cli tool.
compatibility: Requires Dart/Flutter SDK and flutter_workspaces_cli to be installed.
license: MIT
metadata: 
   author: thiagoevoa
   version: "1.0.0"
   triggers:
      keywords: [create, flutter, project, workspaces, template]
---

# Create Flutter Workspaces Project

Use this skill when the user wants to create a new Flutter project. This skill leverages the `flutter_workspaces_cli` command-line tool.

## Prerequisites
- The user must have the Flutter SDK installed.
- The `flutter_workspaces_cli` package must be installed globally (e.g., `dart pub global activate flutter_workspaces_cli`).

## Instructions
1. Check if the `flutter_workspaces_cli` command is available in the user's path.
2. If available, execute the following command, passing the requested project name:
   `flutter_workspaces_cli create <project_name>`
3. If the command is not found, advise the user to run `dart pub global activate flutter_workspaces_cli` and try again.

## Command
```
flutter_workspaces_cli create {{project_name}}
```

## Parameters
- `project_name` (string, required): The name of the new Flutter project.

## Examples
- User says: "Create a new flutter app called 'my_cool_app' using workspaces"
- Action: `flutter_workspaces_cli create my_cool_app`