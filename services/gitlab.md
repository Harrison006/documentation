# Gitlab Install

Installing gitlab can be easily done in these steps

```bash
sudo apt-get update
sudo apt-get install -y curl openssh-server ca-certificates tzdata perl
```

```bash
 curl https://packages.gitlab.com/install/repositories/gitlab/gitlab-ee/script.deb.sh | sudo bash
```

```bash
 sudo EXTERNAL_URL="https://gitlab.example.com" apt-get install gitlab-ee
 ```

This is the most basic setup

Once installed run

```bash
cat /etc/gitlab/initial_root_password
```

and that will give you a root password
