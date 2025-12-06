# SSH & Git Profile Switcher (macOS)

A simple Zsh script to automate switching between two GitHub profiles (e.g., Work vs. Personal) on macOS.

It handles:
1. Overwriting `~/.ssh/config` to point to the correct identity file.
2. Flushing and reloading SSH keys in the authentication agent.
3. Updating global Git configuration (`user.name` and `user.email`).
4. Verifying the connection to GitHub.

**Note:** This script is designed specifically for **macOS** as it utilizes the `--apple-use-keychain` flag for SSH key management.

## Setup

1. Copy the script file to your home directory (e.g., `~/.ssh_switcher`).
2. Open the file and edit the **CONFIGURATION** section at the top with your specific paths and details:
   - SSH Key paths
   - Git Usernames
   - Git Emails
3. Add the following line to your `~/.zshrc` file to load the function on shell startup:

   ```bash
   source ~/.ssh_switcher
   ```

4. Apply the changes:

   ```bash
   source ~/.zshrc
   ```

## Usage

Switch to your Personal profile:

```bash
login personal
```

Switch to your Work profile:

```bash
login work
```

The script will automatically verify authentication with GitHub (`ssh -T`) and display the current global Git user config after switching.

## Example Output

```text
user@macbook ~ % login personal
Switching to PERSONAL context...
Identity added: /Users/user/.ssh/id_rsa_personal (personal@example.com)
Done. Switched to Personal identity.
Verifying GitHub connection...
Hi PersonalUser! You've successfully authenticated, but GitHub does not provide shell access.
Current Global Git Config:
user.name=PersonalUser
user.email=personal@example.com

user@macbook ~ % login work
Switching to WORK context...
Identity added: /Users/user/.ssh/id_rsa_work (work@example.com)
Done. Switched to Work identity.
Verifying GitHub connection...
Hi WorkUser! You've successfully authenticated, but GitHub does not provide shell access.
Current Global Git Config:
user.name=WorkUser
user.email=work@example.com
```
