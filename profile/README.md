
# Git Workflow for [Project Name]

## Branching Strategy

This project follows a structured Git workflow to ensure smooth development and deployment processes.

### Main Branches
1. **`main`**:
   - Contains production-ready code.
   - Only receives changes from the `develop` branch after testing.
   - Direct commits are not allowed.

2. **`develop`**:
   - Used for active development and integration of new features.
   - Contains code that is functional but might not be fully production-ready.
   - Changes are merged here from feature or bugfix branches.

### Feature Branches
- **Naming Convention**:  
  Branches for new features should follow this pattern:  
  `feature/<feature-name>`

  Examples:
  - `feature/landing-page`
  - `feature/user-authentication`

- Always branch off from `develop`:
  ```bash
  git checkout develop
  git checkout -b feature/<feature-name>
  ```

- Once the feature is complete, create a pull request to merge it into `develop`.

### Bugfix Branches
- **Naming Convention**:  
  Branches for bug fixes should follow this pattern:  
  `bugfix/<bug-name>`

  Examples:
  - `bugfix/fix-login-error`
  - `bugfix/typo-homepage`

- Always branch off from `develop` (or `main` for critical hotfixes).

---

## Workflow Steps

### 1. Setting Up the Project
1. Clone the repository:
   ```bash
   git clone <repository-url>
   ```
2. Checkout the `develop` branch:
   ```bash
   git checkout develop
   ```

---

### 2. Adding a New Feature
1. Create a new feature branch from `develop`:
   ```bash
   git checkout -b feature/<feature-name>
   ```
2. Work on the feature and commit your changes:
   ```bash
   git add .
   git commit -m "feat: add <feature-description>"
   ```
3. Push your branch to remote:
   ```bash
   git push origin feature/<feature-name>
   ```
4. Create a pull request to merge into `develop`.

---

### 3. Fixing Bugs
1. Create a new bugfix branch from `develop`:
   ```bash
   git checkout -b bugfix/<bug-name>
   ```
2. Fix the bug and commit your changes:
   ```bash
   git add .
   git commit -m "fix: resolve <bug-description>"
   ```
3. Push your branch to remote:
   ```bash
   git push origin bugfix/<bug-name>
   ```
4. Create a pull request to merge into `develop`.

---

### 4. Testing and Merging
- All changes in `develop` must be tested before merging into `main`.
- When a release is ready:
  1. Create a pull request to merge `develop` into `main`.
  2. Tag the release in `main` after merging:
     ```bash
     git tag -a v<version> -m "Release <version>"
     git push origin v<version>
     ```

---

### 5. Hotfix for Critical Issues
1. Create a new hotfix branch from `main`:
   ```bash
   git checkout main
   git checkout -b hotfix/<hotfix-name>
   ```
2. Fix the issue and commit your changes:
   ```bash
   git add .
   git commit -m "hotfix: fix <issue-description>"
   ```
3. Push the hotfix branch and create a pull request to merge into `main` and `develop`.

---

## Commit Message Convention
Follow the **Conventional Commits** format:
- `feat`: A new feature (e.g., `feat: add user authentication`)
- `fix`: A bug fix (e.g., `fix: resolve login error`)
- `refactor`: Code refactoring without changing functionality.
- `docs`: Documentation updates (e.g., `docs: update README.md`).
- `test`: Adding or updating tests (e.g., `test: add unit tests for login`).
- `chore`: Miscellaneous changes (e.g., `chore: update dependencies`).

---

## Pull Request Guidelines
1. Always create pull requests for merging changes.
2. Assign reviewers to the pull request.
3. Ensure the pull request passes all tests before merging.
4. Use descriptive titles and include context in the pull request description.

---

## Commands Reference
### Create a New Branch
```bash
git checkout develop
git checkout -b <branch-name>
```

### Merge Branch into `develop` or `main`
1. Switch to the target branch:
   ```bash
   git checkout develop
   ```
2. Merge the feature/bugfix branch:
   ```bash
   git merge <branch-name>
   ```

### Delete a Branch
- Locally:
  ```bash
  git branch -d <branch-name>
  ```
- Remotely:
  ```bash
  git push origin --delete <branch-name>
  ```

---

## Example Workflow
1. Start working on a feature:
   ```bash
   git checkout develop
   git checkout -b feature/new-feature
   ```
2. Push changes and create a pull request:
   ```bash
   git push origin feature/new-feature
   ```
3. Merge into `develop`, test, and release to `main`.


