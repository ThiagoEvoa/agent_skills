---
name: create-dart-back-end-project
description: Initializes a new Dart backend template project using the dart_frog tool.
compatibility: Requires Dart and dart_frog to be installed.
license: MIT
metadata: 
   author: thiagoevoa
   version: "1.0.0"
   triggers:
      keywords: [create, dart, project, back-end, template]
---

# Create Dart Backend Project

Use this skill when the user wants to create a new Dart backend project. This skill leverages the `dart_frog` command-line tool.

## Prerequisites
- The user must have the Dart installed.
- The `dart_frog` package must be installed globally (e.g., `dart pub global activate dart_frog`).

## Instructions
1. Check if the `dart_frog` command is available in the user's path.
2. If available, execute the following command, passing the requested project name:
   `dart_frog create <project_name>`
3. If the command is not found, advise the user to run `dart pub global activate dart_frog` and try again.

## Command
```
dart_frog create {{project_name}}
```

## Parameters
- `project_name` (string, required): The name of the new Dart backend project.

## Examples
- User says: "Create a new dart backend called 'my_cool_app'"
- Action: `dart_frog create my_cool_app`