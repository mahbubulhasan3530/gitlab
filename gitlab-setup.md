🚀 GitLab Runner Setup for CI/CD
This guide walks you through installing and registering a GitLab Runner for use in your CI/CD pipelines.

📥 Install GitLab Runner
sudo curl -L --output /usr/local/bin/gitlab-runner https://gitlab-runner-downloads.s3.amazonaws.com/latest/binaries/gitlab-runner-linux-amd64
sudo chmod +x /usr/local/bin/gitlab-runner


👤 Create GitLab Runner User
sudo useradd --comment 'GitLab Runner' --create-home gitlab-runner --shell /bin/bash
🛠 Install and Start GitLab Runner Service
sudo gitlab-runner install --user=gitlab-runner --working-directory=/home/gitlab-runner
sudo gitlab-runner start


🐳 Docker Permissions (Optional if using Docker)
sudo usermod -aG docker gitlab-runner
sudo service docker restart


🧹 Optional Cleanup
Comment out the screen-clear commands in .bash_logout to avoid interruptions:

sudo nano /home/gitlab-runner/.bash_logout
Replace contents with:

# ~/.bash_logout: executed by bash(1) when login shell exits.

# when leaving the console clear the screen to increase privacy

#if [ "$SHLVL" = 1 ]; then
#    [ -x /usr/bin/clear_console ] && /usr/bin/clear_console -q
#fi
📊 Check Runner Status
sudo gitlab-runner status
📝 Register Runner with GitLab
Go to your GitLab project ➝ Settings > CI/CD > Runners
Expand Runners section and click "New project runner"
Set a tag, generate a token, and copy the URL & token
📸 Example:

New Project Runner

🔗 Run the following on your server:
sudo gitlab-runner register
URL: https://gitlab.com
Token: glrt-L5c-Xi4mPFsMw-_omzhW
Executor: shell
📸 Registration Step Example:

Registering GitLab Runner

✅ Done
Your GitLab Runner is now ready to execute CI/CD jobs!

📚 Resources
GitLab CI/CD Docs
GitLab Runner Installation Guide