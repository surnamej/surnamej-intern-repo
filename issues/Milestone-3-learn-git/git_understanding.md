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
## Debugging with git bisect
### Goal
Learn how to use git bisect to identify which commit introduced a bug in a project.

## Tasks
- [x] Research git bisect and how it helps in debugging.
`git bisect` is a binary search tool built into Git that helps find the specific commit where a bug was introduced. It automates the process of checking commits between a known good state and a known bad state.

- [x] Create a test scenario:
  - Make a series of commits in your test repo.
  - Introduce a bug in one of the commits.
  ```bash
  mkdir bisect-test && cd bisect-test
  git init
  echo "Hello World" > app.txt
  git add .
  git commit -m "Initial commit: Add app.txt"

  # Add good commits
  echo "Feature A" >> app.txt
  git commit -am "Add Feature A"

  echo "Feature B" >> app.txt
  git commit -am "Add Feature B"

  # Introduce a bug
  echo "BUGGY CODE" >> app.txt
  git commit -am "Introduce bug in app.txt"

  # More commits
  echo "Feature C" >> app.txt
  git commit -am "Add Feature C"
  ```
  - Use git bisect to track down the commit that introduced the issue.
  ```bash
  git bisect start
  git bisect bad  # HEAD is bad (bug present)

  git log --oneline # To investigate commit-hash
  git bisect good <commit-hash>  # Use hash of commit where bug wasn't present

  # Git will now checkout various commits for testing.
  # At each step:
  cat app.txt
  # If bug is present: `git bisect bad`
  # If bug not present: `git bisect good`

  # When Git finds the culprit, Git will print:
  <commit-hash> is the first bad commit

  # After narrowing down:
  git bisect reset  # Reset back to your original HEAD

  ```

- [x] Experiment using your Git desktop client (or CLI if preferred).
- [x] Write reflections in git_understanding.md:
  - What does git bisect do?
  `git bisect` uses binary search to efficiently find the specific commit that introduced a bug. Instead of checking every commit one by one, it narrows down the range by checking the midpoint each time, cutting the number of steps dramatically.

  - When would you use it in a real-world debugging situation?
  Use `git bisect` when:
    - You know the last time your code worked correctly.
    - A bug appears at some point afterward.
    - You want to identify the exact commit that introduced the issue.

  - How does it compare to manually reviewing commits?
    - Manual review is slow and error-prone, especially in large projects.
    - `git bisect` is fast and automated, often needing just a few checks to pinpoint the problem.

- [x] Commit and push your changes to GitHub.
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
## Merge Conflicts & Conflict Resolution
### Goal
Understand what merge conflicts are, why they happen, and how to resolve them.

## Tasks
- [x] Research what causes merge conflicts in Git.
Merge conflicts happen when:
  - Two branches have changes in the same part of a file.
  - Git cannot automatically determine which change to keep. This typically occurs when two people (or the same person on different branches) make edits to the same lines in the same file.

- [x] Create a merge conflict in your test repo by:
  - Creating a branch and editing a file.
  ```bash
  git checkout -b feature-branch
  ```
  Edit a file (e.g., example.txt) and change one of lines to: `This is the feature branch edit.`
  Add, commit and push the change:
  ```bash
  git add example.txt
  git commit -m "Edit from feature branch"
  git push origin feature-branch
  ```
  - Switching back to main, making a conflicting edit in the same file, and committing it.
  Switch back to main:
  ```bash
  git checkout main
  ```
  Edit the same line in example.txt `This is the main branch edit.`, but change it differently, then commit that change:
  ```bash
  git add example.txt
  git commit -m "Edit from main branch"
  ```
  - Merging the branch back into main.
  ```bash
  git merge feature-branch
  ```
  Git will throw a conflict:
  `CONFLICT (content): Merge conflict in example.txt`

- [x] Use your Git desktop client to resolve the conflict.
- [x] Write about your experience in git_understanding.md:
  - What caused the conflict?
  The conflict was caused by editing the same line in `example.txt` on both `main` and `feature-branch`. Git couldn't automatically decide which version to keep.
  - How did I resolve it?
  I used GitHub Desktop to review the changes. I chose to manually combine the edits into one line that made sense, removed the conflict markers, and marked the file as resolved. Then I committed the merge.
  - What did I learn?
  I learned how Git handles conflicting changes and how to manually resolve them using a Git desktop client. Merge conflicts seem scary, but they’re just Git’s way of asking for help when it’s unsure what changes to keep.

- [x] Commit and push your changes to GitHub.
___________________________________________________________
## Branching & Team Collaboration
### Goal
Understand the importance of branching, avoiding direct pushes to main, and following a structured review process.

## Tasks
- [x] Create a new branch in your Git desktop client (e.g., GitHub Desktop, VS Code, SourceTree).
```bash
git checkout -b branch-test
```
or if you have a'ready had a branch:
```bash
git checkout branch-test
```
- [x] Make a small change in your repo and commit it to the new branch.
I edit a file like team.txt or README.md and add something simple like `This is a collaboration test on a new branch.`, then stage the commit:
```bash
git add .
git commit -m "Add test update for branching practice"
```
- [x] Switch back to main and check that your changes are not there.
```bash
git checkout main
```
Check the file that is changed — the update should not be there. I use `git log --oneline`. I don’t see the commit message I added (like "Add test update for branching practice"), that confirms the commit isn’t in main. This shows how branches isolate changes.

- [x] Reflect on why teams use branches instead of pushing directly to main in git_understanding.md:
  - Why is pushing directly to main problematic?
  Pushing directly to main can introduce errors into the production code without peer review. If everyone pushes to main, bugs and breaking changes might be introduced before they’re tested or reviewed, leading to instability.

  - How do branches help with reviewing code?
  Branches allow developers to isolate work on specific features or fixes. When a branch is ready, a pull request can be created for others to review the code, suggest changes, or approve it. This makes collaboaration safer and more organized.

  - What happens if two people edit the same file on different branches?
  If two people edit the same file (especially the same lines), Git may not know how to automatically merge them. This results in a merge conflict, and someone will nedd to manually resolve it by choosing which version to keep.

- [x] Commit and push your changes to GitHub.
___________________________________________________________
## Git Concepts: Staging vs. Committing
### Goal
Understand the difference between staging and committing in Git by experimenting in your own repository.

## Tasks
- [x] Research the difference between staging and committing.
  - Staging (`git add`):
    Prepares specific changes (files or lines) to be committed. Think of it as a "shopping cart" of changes you're ready to save.

  - Committing (`git commit`):
    Takes all staged changes and permanently records them in the project’s history with a message. It's like checking out your shopping cart and printing a receipt.

- [x] Experiment with adding and committing files in your repo using either:
  - The terminal (git add / git commit)
  - A Git desktop client (e.g., GitHub Desktop, VS Code Git integration).
- [x] Modify a file and try the following:
  - Stage it but don’t commit (git add <file> or equivalent in your client)
  ```bash
  git add stage-learn.txt
  ```
  - Check the status (git status).
  Output said:
  ```
  On branch main

  No commits yet

  Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
        new file:   stage-learn.txt
  ```
  - Unstage the file (git reset HEAD <file> or equivalent).
  Output shown:
  ```
  Unstaged changes after reset:
  M       stage-learn.txt
  ```
  - Commit the file and observe the difference.

- [x] Write a summary in git_understanding.md:
  - What is the difference between staging and committing?
    - **Staging** is selecting which changes you want to include in your next commit.
    - **Committing** saves the staged changes to the Git history with a message.

  - Why does Git separate these two steps?
    Separating staging from committing gives me more control. I can:
    - Choose which changes to commit.
    - Group related changes together.
    - Review everything before making it permanent.

  - When would you want to stage changes without committing?
    - When I am still working but want to save progress in the index.
    - When I want to commit only part of my edits (e.g., using `git add -p`).
    - When collaborating and preparing a clean commit history before pushing.

- [x] Commit and push your changes to GitHub.
