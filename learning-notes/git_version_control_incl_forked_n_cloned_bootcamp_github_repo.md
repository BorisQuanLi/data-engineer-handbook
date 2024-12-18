# Git Version Control

## Table of Contents

1. **Git Version Control**
   - **Initializing a Git Repository**
     - How to initialize an empty Git repository using `git init`.
   - **Renaming the Initial Branch to main**
     - Instructions on renaming the default branch from `master` to `main`.
   - **Handling Submodules**
     - **Adding a Submodule**
       - Steps to add an embedded repository as a submodule.
     - **Updating Submodules**
       - **Pulling the Latest Changes in the Submodule**
         - How to pull the latest changes in a submodule.
       - **Verifying the Default Branch**
         - How to verify which branch will be pulled by default.
       - **Updating All Submodules from the Main Repository**
         - Steps to update all submodules from the main repository.
   - **Committing Changes**
     - **Review the Staged Changes**
       - Ensuring all changes you want to commit are staged.
     - **Commit the Changes**
       - How to commit changes with a descriptive message.
     - **Add the Untracked File**
       - Instructions on adding and committing an untracked file.
   - **Best Practices for Committing Changes**
     - Benefits of committing changes in logical, manageable chunks.
   - **Working in the Cloned Submodule**
     - **Creating a Development Branch**
       - How to create a separate branch for development.
     - **Making Changes and Committing**
       - Steps to make changes and commit them in the development branch.
     - **Pushing Changes and Creating a Pull Request**
       - How to push changes and create a pull request.
     - **Updating the Outer Repository**
       - Steps to update the outer repository to track new commits.
     - **Avoiding Unnecessary Pull Requests in the Outer Repository**
       - Tips to avoid generating unnecessary pull requests.
   - **Pushing to Your Fork**
     - **Fork the Repository**
       - How to create a fork of the main repository on GitHub.
     - **Add Your Fork as a Remote**
       - Steps to add your fork as a remote repository.
     - **Update the Remote URL**
       - How to update the remote URL with your GitHub token.
     - **Push the Development Branch to Your Fork**
       - Instructions on pushing the development branch to your fork.
   - **Generating a Pull Request**
     - Steps to create a pull request on GitHub.
   - **Integrating the Forked Repository**
     - **Forking the Repository and Adding as Remote**
       - How to fork the repository and add it as a remote.
     - **Push the Development Branch to Your Fork**
       - Instructions on pushing the development branch to your fork.
   - **Making New Commits and Pushing to the Remote Repository**
     - Workflow for making new commits and pushing them to the remote repository.
   - **Renaming a File and Committing the Changes**
     - Steps to rename a file and commit the changes.

## Initializing a Git Repository

This command initializes an empty Git repository.
```sh
git init
```

### Context
```sh
$ git init
hint: Using 'master' as the name for the initial branch. This default branch name
hint: is subject to change. To configure the initial branch name to use in all
of your new repositories, which will suppress this warning, call:
hint:
hint:   git config --global init.defaultBranch <name>
hint:
hint: Names commonly chosen instead of 'master' are 'main', 'trunk' and
'hint: development'. The just-created branch can be renamed via this command:
hint:
hint:   git branch -m <name>
Initialized empty Git repository in /mnt/c/Users/Boris_Li/OneDrive/bootcamps/Zach-Wilson-Data-Engineering-Bootcamp/.git/
(zach-wilson-data-eng-venv) boris-ubuntu-22-04@2212-Windows11:/mnt/c/Users/Boris_Li/OneDrive/bootcamps/Zach-Wilson-Data-Engineering-Bootcamp$ git branch -m main
```

## Renaming the Initial Branch to main

The default branch name is `master`, but you can change it to `main`:
```sh
git branch -M main
```

## Handling Submodules

### Adding a Submodule

1. **Force Remove the Embedded Repository from the Index**:
   ```sh
   git rm --cached -f bootcamp-github-repo/data-engineer-handbook
   ```

2. **Add the Embedded Repository as a Submodule**:
   ```sh
   git submodule add https://github.com/DataExpert-io/data-engineer-handbook.git bootcamp-github-repo/data-engineer-handbook
   ```

3. **Commit the Changes**:
   ```sh
   git add .
   git commit -m "Added data-engineer-handbook as a submodule"
   ```

### Updating Submodules

#### Pulling the Latest Changes in the Submodule

1. **Navigate to the Submodule Directory**:
   ```sh
   cd bootcamp-github-repo/data-engineer-handbook
   ```

2. **Pull the Latest Changes**:
   ```sh
   git pull
   ```

#### Verifying the Default Branch

To verify which branch will be pulled by default, you can check the current branch:
```sh
git branch
```
The current branch will be marked with an asterisk (*). If it's `main`, then `git pull` will pull from `origin main`.

#### Updating All Submodules from the Main Repository

1. **Navigate to the Main Repository**:
   ```sh
   cd /mnt/c/Users/Boris_Li/OneDrive/bootcamps/Zach-Wilson-Data-Engineering-Bootcamp
   ```

2. **Update All Submodules**:
   ```sh
   git submodule update --remote
   ```

3. **Commit the Updated Submodule References**:
   ```sh
   git commit -am "Updated submodule references"
   ```

## Committing Changes

### Review the Staged Changes

Ensure that all the changes you want to commit are staged.

### Commit the Changes

```sh
git commit -m "Initial commit with the cloned bootcamp's GitHub repo as a submodule, among files"
```

### Add the Untracked File

If you want to include the untracked file `learning-notes/git_version_control_incl_forked_n_cloned_bootcamp_github_repo.md`, you can add it and commit again:
```sh
git add learning-notes/git_version_control_incl_forked_n_cloned_bootcamp_github_repo.md
git commit -m "Added git version control notes"
```

## Best Practices for Committing Changes

In a production environment, it is generally a good practice to commit changes in logical, manageable chunks rather than waiting for a large batch of changes. This approach has several benefits:

1. **Clarity**: Smaller, focused commits make it easier to understand the history and purpose of changes.
2. **Traceability**: It is easier to trace and debug issues when changes are committed incrementally.
3. **Collaboration**: Smaller commits facilitate better collaboration among team members, as changes are integrated more frequently.
4. **Revertibility**: If an issue arises, it is easier to revert a smaller commit without affecting unrelated changes.

For the file `git_version_control_incl_forked_n_cloned_bootcamp_github_repo.md`, it is appropriate to commit it separately if it represents a distinct, complete piece of work.

## Working in the Cloned Submodule

### Creating a Development Branch

When working on a pull request or local development in the submodule, it is best to create a separate branch for your changes:
```sh
cd bootcamp-github-repo/data-engineer-handbook
git checkout -b boris/dev
```

### Making Changes and Committing

Make your changes in the `boris/dev` branch and commit them:
```sh
git add .
git commit -m "Made changes in the dev branch"
```

### Pushing Changes and Creating a Pull Request

Push your changes to the remote repository and create a pull request:
```sh
git push origin boris/dev
```

### Updating the Outer Repository

After making changes in the submodule, update the outer repository to track the new commit:
```sh
cd /mnt/c/Users/Boris_Li/OneDrive/bootcamps/Zach-Wilson-Data-Engineering-Bootcamp
git add bootcamp-github-repo/data-engineer-handbook
git commit -m "Updated submodule to latest commit"
```

### Avoiding Unnecessary Pull Requests in the Outer Repository

To avoid generating unnecessary pull requests in the outer repository while keeping track of changes in the submodule, follow these steps:

1. **Work in the Submodule**:
   Perform all development work within the submodule's repository. This keeps the outer repository clean and focused on tracking submodule references.

2. **Commit and Push Changes in the Submodule**:
   Commit and push changes to the submodule's remote repository. Create pull requests as needed within the submodule's repository.

3. **Update the Outer Repository**:
   Only update the outer repository when you need to track a new commit in the submodule. This minimizes the number of changes in the outer repository.
   ```sh
   cd /mnt/c/Users/Boris_Li/OneDrive/bootcamps/Zach-Wilson-Data-Engineering-Bootcamp
   git add bootcamp-github-repo/data-engineer-handbook
   git commit -m "Updated submodule to latest commit"
   ```

### Pushing to Your Fork

If you want to keep a backup of your work or share it with others, you can push the branch to your fork of the repository instead of the main repository.

1. **Fork the Repository**:
   - Create a fork of the main repository on GitHub. This will create a copy of the repository under your GitHub account.

2. **Add Your Fork as a Remote**:
   - Add your fork as a remote repository in your local Git configuration.
   ```sh
   git remote add borisli-fork https://github.com/BorisQuanLi/data-engineer-handbook.git
   ```

3. **Update the Remote URL**:
   - Use the `git remote set-url` command to update the remote URL with your GitHub token.
   ```sh
   git remote set-url borisli-fork https://<GitHub-token>@github.com/BorisQuanLi/data-engineer-handbook.git
   ```

4. **Push the Development Branch to Your Fork**:
   - Push the development branch to your fork instead of the main repository.
   ```sh
   git push borisli-fork boris/dev
   ```

### Example Commands

1. **Fork the Repository**:
   - Go to the main repository on GitHub and click the "Fork" button to create a fork under your GitHub account.

2. **Add Your Fork as a Remote**:
   ```sh
   git remote add borisli-fork https://github.com/BorisQuanLi/data-engineer-handbook.git
   ```

3. **Update the Remote URL**:
   ```sh
   git remote set-url borisli-fork https://<GitHub-token>@github.com/BorisQuanLi/data-engineer-handbook.git
   ```

4. **Push the Development Branch to Your Fork**:
   ```sh
   git push borisli-fork boris/dev
   ```

### Generating a Pull Request

1. **Navigate to Your Fork on GitHub**:
   - Go to your fork of the repository on GitHub.

2. **Create a Pull Request**:
   - Click the "Compare & pull request" button.
   - Ensure the base repository is the original repository (e.g., `DataExpert-io/data-engineer-handbook`) and the base branch is `main`.
   - Ensure the head repository is your fork (e.g., `BorisQuanLi/data-engineer-handbook`) and the compare branch is your development branch (e.g., `boris/dev`).
   - Add a title and description for your pull request.
   - Click the "Create pull request" button.

3. **Address Feedback**:
   - Address any feedback from the code reviewers by making additional commits to your development branch and pushing them to your fork. The PR will automatically update with the new commits.

## Integrating the Forked Repository

### Forking the Repository and Adding as Remote

1. **Fork the Repository**:
   - Go to the main repository on GitHub and click the "Fork" button to create a fork under your GitHub account.

2. **Add Your Fork as a Remote**:
   - Add your fork as a remote repository in your local Git configuration.
   ```sh
   cd /mnt/c/Users/Boris_Li/OneDrive/bootcamps/Zach-Wilson-Data-Engineering-Bootcamp/bootcamp-github-repo/data-engineer-handbook
   git remote add borisli-fork https://github.com/BorisQuanLi/data-engineer-handbook.git
   ```

3. **Update the Remote URL**:
   - Use the `git remote set-url` command to update the remote URL with your GitHub token.
   ```sh
   git remote set-url borisli-fork https://<GitHub-token>@github.com/BorisQuanLi/data-engineer-handbook.git
   ```

4. **Push the Development Branch to Your Fork**:
   - Push the development branch to your fork instead of the main repository.
   ```sh
   git push borisli-fork boris/dev
   ```

### Example Commands

1. **Fork the Repository**:
   - Go to the main repository on GitHub and click the "Fork" button to create a fork under your GitHub account.

2. **Add Your Fork as a Remote**:
   ```sh
   cd /mnt/c/Users/Boris_Li/OneDrive/bootcamps/Zach-Wilson-Data-Engineering-Bootcamp/bootcamp-github-repo/data-engineer-handbook
   git remote add borisli-fork https://github.com/BorisQuanLi/data-engineer-handbook.git
   ```

3. **Update the Remote URL**:
   ```sh
   git remote set-url borisli-fork https://<GitHub-token>@github.com/BorisQuanLi/data-engineer-handbook.git
   ```

4. **Push the Development Branch to Your Fork**:
   ```sh
   git push borisli-fork boris/dev
   ```

### Successful Push Confirmation

After executing the push command, you should see a confirmation message similar to this:

```sh
$ git push borisli-fork boris/dev
Total 0 (delta 0), reused 0 (delta 0), pack-reused 0
remote:
remote: Create a pull request for 'boris/dev' on GitHub by visiting:
remote:      https://github.com/BorisQuanLi/data-engineer-handbook/pull/new/boris/dev
remote:
To https://github.com/BorisQuanLi/data-engineer-handbook.git
 * [new branch]      boris/dev -> boris/dev
```

## Making New Commits and Pushing to the Remote Repository

Yes, going forward, you can use `git push` to store new commits in the remote server (GitHub). Since you have already set up the remote repository and pushed your development branch, subsequent pushes will work as expected.

Here is a typical workflow for making new commits and pushing them to the remote repository:

1. **Make Changes**:
   - Make changes to your files in the local repository.

2. **Stage the Changes**:
   - Stage the changes using `git add`.
   ```sh
   git add <file1> <file2> ...
   ```

3. **Commit the Changes**:
   - Commit the changes with a descriptive message.
   ```sh
   git commit -m "Your commit message"
   ```

4. **Push the Changes**:
   - Push the changes to the remote repository.
   ```sh
   git push borisli-fork boris/dev
   ```

### Example Commands

1. **Make Changes**:
   - Edit your files as needed.

2. **Stage the Changes**:
   ```sh
   git add <file1> <file2> ...
   ```

3. **Commit the Changes**:
   ```sh
   git commit -m "Your commit message"
   ```

4. **Push the Changes**:
   ```sh
   git push borisli-fork boris/dev
   ```

## Renaming a File and Committing the Changes

### Rename the File in the Filesystem

Use the `mv` command to rename the file in the filesystem.
```sh
mv learning-notes/git_version_control_incl_cloned_bootcamp_github_repo.md learning-notes/git_version_control_incl_forked_n_cloned_bootcamp_github_repo.md
```

### Track the Rename in Git

Use the `git mv` command to track the rename in Git.
```sh
git mv learning-notes/git_version_control_incl_cloned_bootcamp_github_repo.md learning-notes/git_version_control_incl_forked_n_cloned_bootcamp_github_repo.md
```

### Stage the Renamed File

Stage the renamed file using `git add`.
```sh
git add learning-notes/git_version_control_incl_forked_n_cloned_bootcamp_github_repo.md
```

### Commit the Changes

Commit the changes with a descriptive message.
```sh
git commit -m "Renamed file to better reflect its content and added detailed instructions"
```

### Example Commands

1. **Rename the File in the Filesystem**:
   ```sh
   mv learning-notes/git_version_control_incl_cloned_bootcamp_github_repo.md learning-notes/git_version_control_incl_forked_n_cloned_bootcamp_github_repo.md
   ```

2. **Track the Rename in Git**:
   ```sh
   git mv learning-notes/git_version_control_incl_cloned_bootcamp_github_repo.md learning-notes/git_version_control_incl_forked_n_cloned_bootcamp_github_repo.md
   ```

3. **Stage the Renamed File**:
   ```sh
   git add learning-notes/git_version_control_incl_forked_n_cloned_bootcamp_github_repo.md
   ```

4. **Commit the Changes**:
   ```sh
   git commit -m "Renamed file to better reflect its content and added detailed instructions"
   ```

### Updated Content for the File
