# Source Code Management

Effective source code management is crucial for collaborative Android development. We utilize Git as our Version Control System (VCS), accessible through command-line or GUI tools like GitHub Desktop.

---

### 1. Branching Strategy

* **Development Branch:**
    * This branch serves as the central integration point for all stable development changes.
####
* **Personal Branches:**
    * Each developer creates personal branches for feature development or bug fixes.
    * **Branch Naming:**
        * Personal branches should adhere to a clear naming convention.
        * Template: `user_feature_or_details` (must be lowercase and using “_” for the separator of each words).
        * Example: `hafizh_test_bank_enhancement`.
        * This format ensures consistency and easy identification of the branch's owner and purpose.

### 2. Commit

* **Commit Message:**
    * Start the commit message title with the corresponding JIRA ticket code, followed by a descriptive title.
    * Template: `emoji [TICKET-123] What's inside the PR`
    * Example: `:sparkles: [FIZ-123] Layouting Login Page`
    * Example: `:bug: [POKA-111][POKA-112][POKA-113] Integration Login, Register`
    * The use of emojis is optional but encouraged for improved readability and clarity.

### 3. Pull Requests (PRs)

* **PR Message:**
    * The PR title can follow the same conventions as commit messages.
    * The PR description should provide detailed information about the changes, including:
        * The purpose of the changes.
        * Any relevant context.
        * Any potential impacts.
    * The PR description can be modified from the commit message to provide additional clarity and context.
####
* **Code Review:**
    * All PRs must undergo code review by teammates or the team lead before being merged.
    * This ensures code quality, consistency, and early detection of potential issues.

### 4. Emojis (Gitmoji)

* **Reference:**
    * We utilize Gitmoji for consistent and visually informative commit messages. Refer to [https://gitmoji.dev/](https://gitmoji.dev/) for a comprehensive list.
####
* **Common Emojis:**
    * `:sparkles:` - New feature
    * `:bug:` - Bug fix
    * `:hammer:` - Enhancement/refactoring
####
* **Usage:**
    * While any emoji can be used, adhering to common Gitmoji conventions improves team communication and code readability.
