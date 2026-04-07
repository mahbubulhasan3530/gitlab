# 🚀 GitLab Runner Setup for CI/CD

This guide walks you through installing and registering a GitLab Runner for use in your CI/CD pipelines.

---

## 📥 Install GitLab Runner

```bash
sudo curl -L --output /usr/local/bin/gitlab-runner \
https://gitlab-runner-downloads.s3.amazonaws.com/latest/binaries/gitlab-runner-linux-amd64

sudo chmod +x /usr/local/bin/gitlab-runner 
```

---

## 👤 Create GitLab Runner User

```bash
sudo useradd --comment 'GitLab Runner' \
--create-home gitlab-runner \
--shell /bin/bash
```

---

## 🛠 Install and Start GitLab Runner Service

```bash
sudo gitlab-runner install \
--user=gitlab-runner \
--working-directory=/home/gitlab-runner

sudo gitlab-runner start
```

---

## 🐳 Docker Permissions (Optional)

> Only required if you plan to use Docker executor

```bash
sudo usermod -aG docker gitlab-runner
sudo service docker restart
```

---

## 🧹 Optional Cleanup

Comment out screen-clear commands to avoid interruptions:

```bash
sudo nano /home/gitlab-runner/.bash_logout
```

Replace contents with:

```bash
# ~/.bash_logout: executed by bash(1) when login shell exits.

# when leaving the console clear the screen to increase privacy

#if [ "$SHLVL" = 1 ]; then
#    [ -x /usr/bin/clear_console ] && /usr/bin/clear_console -q
#fi
```

---

## 📊 Check Runner Status

```bash
sudo gitlab-runner status
```

---

## 📝 Register Runner with GitLab

### Step 1: Get Credentials

- Go to your GitLab project  
- Navigate to: **Settings → CI/CD → Runners**  
- Click **"New project runner"**  
- Copy:
  - URL  
  - Token  

---

### Step 2: Register Runner

```bash
sudo gitlab-runner register
```

Provide the following:

```
URL: https://gitlab.com
Token: <your-runner-token>
Executor: shell
```

---

## ✅ Done

Your GitLab Runner is now ready to execute CI/CD jobs 🎉

---

## 📚 Resources

- GitLab CI/CD Documentation  
- GitLab Runner Installation Guide  
