---
name: code-reviewer
description: Analyzes changed code against Clean Code, SOLID, Design Patterns and Composition over Inheritance.
compatibility: Requires Git.
license: MIT
metadata: 
   author: thiagoevoa
   version: "1.0.0"
   triggers:
     keywords: [review, best practices, refactor, analyze, improve]
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
   - **SOLID:** Are the changes adhering to Single Responsibility Principle, Open/Closed Principle and Dependency Inversion Principle?
   - **Composition:** Are you using `Mixins` or `Delegates` where class inheritance might lead to fragile base classes?
   - **Clean Code:** Check for Meaningful Naming, Single Responsibility Principle, DRY (Don't Repeat Yourself), KISS (Keep It Simple, Stupid), Small Functions in the *modified code*.
4. **Report:** Generate a summary of issues found specifically in the changeset and provide suggested "Refactoring" code blocks.

## Workflow
1. Run `git diff` on the working directory.
2. Filter the output to target only the changed chunks.
3. Provide feedback formatted as:
   - **File:** [filename]
   - **Issue:** [Description of violation]
   - **Refactor:** [Suggested improvement]

## Parameters
- `git_diff` (string, optional): The diff output. If not provided, the agent should attempt to run `git diff` in the current context.

## Examples
- User says: "Review my code changes"
- Action: `git diff` -> Analyze results -> Provide improvement plan.