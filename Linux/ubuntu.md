# Post install Things

## Bash Script
Using a bash script to install things such as Oh-my-Posh

```bash
#!
sudo apt install -y unzip

## Install Oh my Posh
sudo wget https://github.com/JanDeDobbeleer/oh-my-posh/releases/latest/download/posh-linux-amd64 -O /usr/local/bin/oh-my-posh
sudo chmod +x /usr/local/bin/oh-my-posh

## Download the themes
mkdir ~/.poshthemes
wget https://github.com/JanDeDobbeleer/oh-my-posh/releases/latest/download/themes.zip -O ~/.poshthemes/themes.zip
unzip ~/.poshthemes/themes.zip -d ~/.poshthemes
chmod u+rw ~/.poshthemes/*.json
rm ~/.poshthemes/themes.zip

eval "$(oh-my-posh --init --shell bash --config ur-theme)"

sudo apt install cockpit

Something along the lines of that would be a usual server install
```
Installing ssh keys would be as simple as adding a cp commmand to copy the authorized_keys file from the nfs share to the machine and under your profile as u

Once cockpit is installed you can join the machine to AD so you can use one login for everything