
# Getting Started with Git and GitHub

## Installing Git
1. **Download Git**: Go to [https://git-scm.com/](https://git-scm.com/) and download Git for your operating system.
2. **Install Git**: Run the downloaded file and follow the installation instructions.
3. **Verify Installation**: Open your command line interface (CLI) and type:
   ```
   git version
   ```
   This checks that Git is installed correctly.

## Initializing a Project with Git
1. **Create a Project Directory**: Make a new folder for your project, named `GIT`.
2. **Create a README File**: Inside the `GIT` folder, create a file named `README.md` and add some initial content.
3. **Initialize Git**: In your CLI, navigate to your project directory (`GIT`) and run:
   ```
   git init
   ```
   This starts a new Git repository in your project folder.

## Setting Up GitHub
1. **Create a GitHub Account**: Visit [GitHub](https://github.com/) and sign up or log in.
2. **Create a New Repository**: On GitHub, create a new repository named `github-tutorial`.

## Connecting Local Git to GitHub
1. **Link Your Project to GitHub**: In your project's CLI, run:
   ```
   git remote add origin https://github.com/piopratama/github-tutorial.git
   ```
   Replace the URL with the one for your GitHub repository.

## Git Configuration
- **Global Configuration**: To view your global Git settings, execute:
  ```
  git config --global --list
  ```
  To set global configurations like your username and email, use:
  ```
  git config --global user.name "Your Name"
  git config --global user.email "your.email@example.com"
  git config --global credential.helper manager
  ```
- **Local Configuration**: For project-specific settings, omit `--global`. Local config overrides global settings.

## Checking Remote URLs
- To check your repository's URL, use:
  ```
  git remote -v
  ```
  This will show if you're using HTTPS or SSH.

## Pushing to GitHub
1. **Add Your Files**: Add all files in the project directory to Git:
   ```
   git add .
   ```
2. **Commit Your Changes**: Commit your changes with a message:
   ```
   git commit -m "Initial commit"
   ```
3. **Set Main Branch**: Rename the current branch to `main`:
   ```
   git branch -M main
   ```
4. **Push to GitHub**: Push your code to GitHub:
   ```
   git push --set-upstream origin main
   ```
   Use `--set-upstream origin main` the first time you push a new branch. Afterwards, you can simply use `git push`.
