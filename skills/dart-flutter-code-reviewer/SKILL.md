---
name: dart-flutter-code-reviewer
description: Analyzes changed code against Clean Code, SOLID, Design Patterns and Composition over Inheritance.
compatibility: Requires Git.
license: MIT
metadata: 
   author: thiagoevoa
   triggers:
     keywords: [review, best practices, refactor, dart code, flutter code]
---

# Code Reviewer

Use this skill to evaluate code changes (`git diff`) against industry-standard architectural principles.

## Objectives
- Ensure compliance with **SOLID** principles.
- Enforce **Clean Code** standards (meaningful naming, small functions).
- Validate Design Patterns.
- Promote **Composition over Inheritance**.

## Instructions
1. **Identify Changes:** Detect modified or added files using `git diff --cached` or a provided diff string.
2. **Analyze:** Perform a targeted review of the diff, focusing on:
   - **SOLID Principles:** For each principle, refer to its corresponding template file to guide your analysis.
     - **Single Responsibility Principle:** See `templates/single_responsible_principle.md`
     - **Open/Closed Principle:** See `templates/open_closed_principle.md`
     - **Liskov Substitution Principle:** See `templates/liskov_substitution_principle.md`
     - **Interface Segregation Principle:** See `templates/interface_segregation_principle.md`
     - **Dependency Inversion Principle:** See `templates/dependency_inversion_principle.md`
   - **Composition over Inheritance:** See `templates/composition.md`. Are you using `Mixins` or `Delegates` where class inheritance might lead to fragile base classes?
   - **Clean Code:** See `templates/clean_code.md`.
3. **Report:** Generate a summary of issues found specifically in the changeset. For each issue, provide a suggested "Refactor" code block.

## Workflow
1. Run `git diff` on the working directory.
2. Filter the output to target only the changed chunks.
3. For each changed chunk, analyze it against the principles outlined in the **Instructions** section. Use the content of the template files as a guide.
4. Provide feedback formatted as:
   - **File:** [filename]
   - **Issue:** [Description of violation, referencing the specific SOLID principle or Clean Code concept]
   - **Refactor:** [Suggested improvement]

## Parameters
- `git_diff` (string, optional): The diff output. If not provided, the agent should attempt to run `git diff` in the current context.

## Examples
- User says: "Review my code changes"
- Action: `git diff` -> Analyze results -> Provide improvement plan.