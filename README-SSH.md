
# Switching from HTTPS to SSH for GitHub

SSH offers a more secure method of connecting to GitHub by using cryptographic keys. Here's how you can set up SSH for your GitHub repository:

## Generating SSH Keys
1. **Generate SSH Keys**: Open your command line interface (CLI) and generate a new SSH key pair (private and public keys) with the command:
   ```
   ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
   ```
   Replace `"your_email@example.com"` with the email address associated with your GitHub account.

2. **Specify Key Storage Path**: Common practice on Windows is to store keys under `C:/Users/your_username/.ssh`. If you already have existing keys, save the new key pair with a different file name or remove the old files.

3. **Copy Public Key to GitHub**: Navigate to your `.ssh` directory, open the file with a `.pub` extension (this is your public key), copy its contents, and add it to your GitHub account under Settings -> SSH and GPG Keys.

## Using SSH with Git
1. **Initialize New Project with SSH**: For new projects, use the following commands:
   ```
   git init
   git remote add origin git@github.com:username/repository.git
   ```
   Replace `git@github.com:username/repository.git` with your repository's SSH link.

2. **Authenticate Using the Private Key**: To push changes, authenticate with your private key using:
   ```
   GIT_SSH_COMMAND="ssh -i /path/to/keys/private_key" git push origin branch-name
   ```

## Managing SSH Keys
1. **Using SSH Agent**: To avoid entering your private key every time, add it to the SSH agent:
   ```
   ssh-add ~/path/to/private_key
   ```
2. **Test Connection to GitHub**: Verify your SSH setup by connecting to GitHub:
   ```
   ssh -T git@github.com
   ```
3. **Persistent SSH Authentication**: To make the SSH agent remember your private key across restarts, create a `config` file in your `.ssh` directory with:
   ```
   # GitHub.com server
   Host github.com
   IdentityFile /path/to/private_key
   ```
   Replace `/path/to/private_key` with the actual path to your private key file.

## Handling Multiple GitHub Accounts
1. **Generate Separate SSH Keys**: If you have multiple GitHub accounts, generate a separate pair of SSH keys for each.
2. **Configure SSH for Multiple Accounts**: Modify your `.ssh/config` file to include both accounts:
   ```
   # GitHub account A
   Host github.com-A
       Hostname github.com
       User username-A
       IdentityFile /path/to/first_private_key

   # GitHub account B
   Host github.com-B
       Hostname github.com
       User username-B
       IdentityFile /path/to/second_private_key
   ```
3. **Test SSH Connection**: Test the connection for each account with:
   ```
   ssh -T git@github.com-A
   ssh -T git@github.com-B
   ```

This guide outlines how to switch from HTTPS to SSH for a more secure connection to GitHub, manage SSH keys, and handle multiple GitHub accounts using SSH.
