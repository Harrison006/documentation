# Disclaimer

Disclaimer all commands are performed on some sort of flavour of ubuntu 20, 22

# Copying a File

In these examples i am just using an ssh directory, dont actually just copy and paste this

### A folder

```bash
cp -d ~/.ssh /etc/your/fake/dir
```

### Copying a simple file
```bash
cp ~/.ssh/id_rsa.pub /mnt/your/fake/dir/
# Or
cp ~/.ssh/id_rsa.pub /mnt/your/fake/dir/authorized_keys

# this is an example of me copying a file and renaming it in the same command
```

# Renaming Cutting/Moving a file

### Renameing a file
```bash
mv ~/.ssh/id_rsa.pub ~/.ssh/authorized_keys
```
### Moving a file
```bash
mv ~/.ssh/id_rsa.pub /etc/your/fake/dir/id_rsa.pub
# Or
mv ~/.ssh/id_rsa.pub /etc/your/fake/dir/authorized_keys
```

# Adding a user

Add the user John

```bash
sudo adduser John
```
Then follow the prompts, the only required info is the password

### Adding that user to the sudo group

```bash
sudo adduser John sudo 
```
Now the user should be a sudo user

This would also apply to another group say docker

```bash
sudo adduser John docker
```