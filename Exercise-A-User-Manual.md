# Exercise A – User Manual Procedure

## Setting Up a GitHub Repository and Making Your First Commit

### Purpose

This procedure explains how to create a new GitHub repository, connect it to a local project folder, and make the first commit. It is written for a first-semester computing student with basic computer skills but little or no experience using Git or GitHub.

## Prerequisites

Before starting, make sure you have:

- A GitHub account.
- Git installed on your computer.
- An internet connection.
- A project folder containing at least one file.
- A terminal such as Git Bash, Command Prompt, PowerShell, or the VS Code terminal.
- Basic knowledge of how to open folders and files on your computer.

## Procedure

### 1. Open GitHub

Open the GitHub website in your web browser.

**Expected result:** The GitHub homepage or your GitHub dashboard appears.

### 2. Sign in

Sign in to your GitHub account.

**Expected result:** Your personal GitHub dashboard is displayed.

### 3. Start a new repository

Click the **New repository** button.

**Expected result:** The "Create a new repository" page opens.

### 4. Enter the repository name

Enter a name for the repository in the **Repository name** field.

**Expected result:** GitHub shows that the repository name is available.

### 5. Choose repository visibility

Select either **Public** or **Private**.

**Expected result:** Your preferred repository visibility is selected.

### 6. Create the repository

Click **Create repository**.

**Expected result:** GitHub creates the repository and displays its setup page.

### 7. Open the terminal

Open Git Bash, Command Prompt, PowerShell, or the VS Code terminal.

**Expected result:** A command-line window appears.

### 8. Navigate to the project

Navigate to your project folder using the `cd` command.

**Expected result:** The terminal location changes to your project folder.

### 9. Initialize Git

Run:

```bash
git init
```

**Expected result:** Git creates a local Git repository inside the project folder.

### 10. Stage the files

Run:

```bash
git add .
```

**Expected result:** All project files are added to the Git staging area.

### 11. Make the first commit

Run:

```bash
git commit -m "Initial commit"
```

**Expected result:** Git creates the first commit containing the staged project files.

### 12. Copy the repository URL

Copy the HTTPS repository URL from GitHub.

**Expected result:** The repository URL is copied to the clipboard.

### 13. Connect the local repository

Run the following command, replacing the example URL with your own repository URL:

```bash
git remote add origin https://github.com/username/repository-name.git
```

**Expected result:** The local project is connected to the GitHub repository.

### 14. Rename the branch

Run:

```bash
git branch -M main
```

**Expected result:** The current branch is named `main`.

### 15. Push the project

Run:

```bash
git push -u origin main
```

**Expected result:** The project files are uploaded to GitHub.

### 16. Verify the upload

Refresh the GitHub repository page.

**Expected result:** The project files and first commit appear in the repository.

## Screenshot Description

A suitable screenshot should show the GitHub repository page after the first successful push. It should clearly display the repository name, uploaded project files, the `main` branch, and the **Initial commit** message next to the latest commit.

An actual screenshot can be placed in the `screenshots` folder if required by the instructor.

## Troubleshooting

### Common Error: Authentication Failed

A beginner may receive an error similar to:

```text
remote: Invalid username or token.
Password authentication is not supported for Git operations.
fatal: Authentication failed
```

GitHub does not accept a normal account password for Git operations over HTTPS. Use a supported authentication method such as GitHub Credential Manager, a personal access token, or SSH authentication. GitHub Credential Manager is generally the easiest option for beginners.
