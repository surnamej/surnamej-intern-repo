# Milestone: Learn Git
## Creating & Reviewing Pull Requests
### Goal
Learn how to create, review, and collaborate on Pull Requests (PRs) in GitHub.

## Tasks
- [x] Research what a Pull Request (PR) is and why it’s used.
  A Pull Request (PR) is a method by which developers can propose changes to a code repository. When you create a PR, you request the repository’s maintainers to review and merge your changes into a target branch (often the main or master branch). PRs serve multiple purposes:
  - They facilitate discussion among team members about code quality, best practices, and potential improvements.
  - They allow multiple developers to work on the same project without conflicting, tracking every change before merging.
  - PRs enable automated testing and manual reviews, ensuring that only tested and reviewed code becomes part of the project.
  
  This process is essential in team workflows, particularly in large projects or open-source initiatives, ensuring that changes are deliberate, traceable, and maintain the project’s integrity.

- [x] Create a new branch in your Git desktop client.
  (Using the Git CLI)
  1. Open the terminal.
  2. Navigate to repository. `cd path/to/repo`
  3. From the current repository, create a new branch (for example, name it feature/small-change). *Tip*: Naming branches clearly (with a prefix like “feature/”, “bugfix/”, etc.) helps others understand the purpose.
  ```bash
  git checkout -b feature/update-readme
  ```
- [x] Make a small change and push the branch to GitHub.
- [x] Open a Pull Request on GitHub:
  - Add a meaningful PR title and description.
  - Link to a related issue (if applicable).
  ```bash
    git add README.md
    git commit
  ```
  Commit -> ( chore: Test pull request workflow 
              Added a small change to verify the pull request process is working correctly.)
  - Push the branch to GitHub.
  ```bash
    git push origin feature/update-readme
  ```
- [x] Review an existing PR in a public open-source repo (e.g., [React PRs](https://github.com/facebook/react/pulls)):
  - Read through comments and discussions.
  - Observe how changes are requested and approved.
    I navigated to the React PR page and picked a PR that caught my interest. The title was clear, and the description gave a good overview of the changes. I really appreciated that the contributor linked it to a related issue, which helped me understand the context right away.
    - Clear Communication Matters: A detailed PR with a clear title, description, and linked issues makes reviewing a lot smoother.
    - Small, Focused Changes Work Best: Incremental commits help in tracing the changes and understanding the rationale behind each step.
    - Team Collaboration is Vital: The back-and-forth between the contributor and reviewers showed me how valuable open dialogue is in refining and improving code.
- [x] Write reflections in git_understanding.md:
  - Why are PRs important in a team workflow?
    - They allow team members to collaborate asynchronously, ensuring everyone is aware of changes and can provide input.
    - PRs introduce code reviews and automated testing to catch potential issues before they affect the main branch.
    - They provide a historical record of changes and the reasoning behind them, which is invaluable for maintaining and evolving the codebase.
  
  - What makes a well-structured PR?
    - A good PR starts with a descriptive title and a detailed explanation of what changes have been made and why.
    - Connecting PRs to relevant issues or tickets helps in tracking the discussion and understanding the context.
    - Keeping PRs small and focused makes them easier to review and reduces the risk of introducing bugs.
    - Including tests and ensuring that your changes don’t break the build is critical.
    - Well-organized, logical commits help the reviewers understand the progression of your changes.

  - What did you learn from reviewing an open-source PR?
    - Seeing how experienced developers suggest improvements and discuss alternative solutions.
    - Recognizing that even small changes often undergo multiple rounds of refinement before being approved.
    - Realizing the role detailed documentation plays in ensuring that everyone understands the purpose behind a change.

- [x] Request feedback on your PR from a peer or mentor
- [x] Merge the PR (if approved) and delete the branch.
___________________________________________________________
## Writing Meaningful Commit Messages
### Goal
Learn how to write clear, meaningful commit messages that improve collaboration and code history readability.

## Tasks
- [x] Research best practices for writing commit messages.
Writing clear and meaningful commit messages is crucial for collaboration and maintaining a readable code history. Here are some best practices:

1. Use the Imperative Mood: Write commit message as if we're giving a command. For example, "Fix bug in user login" instead of "Fixed bug in user login".
2. Keep the Subject Line Short and Descriptive: Limit the subject line to 50 characters or less. Capitalize the first word and do not end with a period.
3. Separate Subject from Body with a Blank Line: If we need to provide more detail, add a blank line between the subject and the body of the commit message.
4. Provide a Detailed Description: Explain the "what" and "why" of the changes, not just the "how". Use bullet points or paragraphs to break down complex changes.
5. Reference Issues and Pull Requests: Link to relevant issues or pull requests by including their numbers (e.g., Closes #123).
6. Use Consistent Formatting: Follow a consistent style guide for commit messages across your team or project.
7. Review Commit Messages: Before finalizing, read through a commit message to ensure it clearly communicates the changes.
8. Avoid Large Commits: Break down large changes into smaller, logical commits to make the history easier to follow.
Source: [How to Write Better Git Commit Messages – A Step-By-Step Guide](https://www.freecodecamp.org/news/how-to-write-better-git-commit-messages/)

- [x] Explore commit histories in an open-source GitHub project (e.g., React, Node.js) and analyze good vs. bad commit messages.
  I noticed that:
  - **Good Commit Messages**: These were typically descriptive, succinct, and provided context regarding why changes were made. They often mentioned the problem and the solution.
  - **Bad Commit Messages**: Commit messages such as “fixed stuff” or “update” lacked any context, making it hard to understand what was truly changed or why it was necessary.

- [x] Make three commits in your repo with different commit message styles:
  - A vague commit message (e.g., "fixed stuff").
    For the first commit, I used a vague message that lacked detail: `Updated file.txt`. This message didn't specify why I updated the following text file, making it unclear to anyone reading the history later.
  - An overly detailed commit message.
    In the second commit, I wrote an overly detailed message that, while informative, was more verbose than necessary:
    ```
    chore: Testing the pull request process for the first time to make sure everything is working correctly. This commit is just a test to check if the pull request system is functioning as expected. I created a new branch, made a small change, and am now committing this to verify that the PR workflow is smooth. Steps taken:
      - Created a new branch from `main`
      - Modified a file to include a minor change
      - Committed the change with this message
      - Pushing the branch to remote to open a PR
    If everything works well, this PR should be reviewed, approved, and merged without issues.
    ```
    Although the message contained a lot of information, it was too detailed for a simple configuration update. It made the history cluttered and harder to quickly scan through when looking for changes.
  - A well-structured commit message.
    For the third commit, I balance a writing clear and structured message:
    ```
    chore: Test pull request workflow
    Added a small change to verify the pull request process is working correctly.
    ```
    This message is concise, explains the problem, states the solution, and references a related issue. It gives anyone reading the history enough context without being too wordy.

- [x] Write reflections in git_understanding.md:
  - What makes a good commit message?
    A good commit message is clear, concise, and provides just enough context for someone else (or future you) to understand what was done and why. It should ideally follow a consistent structure (subject line, body, and footer if necessary) and reference any issues or bugs it addresses.

  - How does a clear commit message help in team collaboration?
    Clear commit messages improve team collaboration by ensuring that everyone, regardless of their familiarity with the project, can quickly understand the evolution of the codebase. They reduce the time spent deciphering changes, make it easier to locate specific updates during debugging, and help maintain an understandable project history.

  - How can poor commit messages cause issues later?
    Poor commit messages, like “fixed stuff,” can lead to confusion, increased debugging time, and difficulties in identifying why certain changes were made. This lack of clarity may also negatively impact teamwork, as other developers might misinterpret the purpose or intent behind changes, potentially causing conflicts or redundant work.
- [x] Commit and push your changes to GitHub.
___________________________________________________________

___________________________________________________________

## Advanced Git Commands & When to Use Them
### Goal
Understand and experiment with advanced Git commands using your preferred Git desktop client.

## Tasks
- [x] Research the following Git commands and test them in your repo:
  - git checkout main -- <file> – Restore a specific file from main without affecting other changes.
  Useful when a single file becomes corrupted or diverges undesirably from the main branch. Rather than resetting the entire branch, this command enables targeted recovery without affecting unrelated work.

  - git cherry-pick <commit> – Apply a specific commit from another branch without merging the whole branch.
  Ideal for situations where a critical bug fix or feature exists in one branch and needs to be replicated in another without merging the entire branch. This ensures that only the desired commit is transferred, preserving the stability of the target branch.

  - git log – View commit history and understand how changes evolved.
  Allows team members to review the chronological evolution of the code, understand why changes were made, and track down the introduction of bugs. It is indispensable when analyzing the commit history during code audits or debugging sessions.

  - git blame <file> – See who last modified each line in a file and when.
  Provides a detailed record of modifications, which is particularly useful for tracing the origin of specific lines of code during troubleshooting or when clarifying the rationale behind a particular change.

- [x] Experiment with each command in your test repo:
  - Modify a file, then restore it using checkout.
  - Commit changes on a branch, then cherry-pick one commit onto main.
  - Use git log to explore the commit history.
  - Use git blame to see past changes in a file.

- [x] Write reflections in git_understanding.md:
  - What does each command do?
  Each command serves a unique role in managing a repository’s history. They offer granular control—for example, restoring one file without disturbing overall branch work or applying a single commit from another branch selectively.

  - When would you use it in a real project (hint: these are all really important in long running projects with multiple developers)?
  In long-running projects with multiple developers, these commands are critical. They help maintain a clean and accurate version history, allow for precise bug fixes, and support better collaboration by providing transparency over who made what changes and when.

  - What surprised you while testing these commands?
  During testing, it became evident that granular commands like git blame offer significant insight into code authorship, which can be instrumental during debugging and code reviews. Additionally, the power of git cherry-pick to isolate a single commit surprised many by simplifying the process of backporting fixes, while git checkout for files proved to be a valuable tool for non-destructive recovery of individual files.

- [x] Commit and push your changes to GitHub.
___________________________________________________________
