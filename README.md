Open Git CMD:

```
cd C:\Users\dell\Desktop\cherry 
git init
git add .
git commit -m “Initial commit”
git remote add origin https://github.com/Madalacharitavya/SE.git
git push -u origin master
git log
git branch branch name
git checkout branch name
git merge branch name
git status
git init
git checkout -b branch name
git add branchname.txt
git commit -m “file name”
git push origin branch name
git status
```

Linux Commands 
```
# List directory contents
ls
# Change directory
cd /home/user/documents
# Print working directory
pwd
# Make directory
mkdir my_folder
# Remove files or directories
rm file.txt
rm -r my_folder
# Copy files or directories
cp file.txt new_file.txt
cp -r my_folder new_folder
# Move or rename files or directories
mv file.txt renamed_file.txt
mv my_folder new_folder_name
# Concatenate and display files
cat file1.txt file2.txt
# Display files one page at a time
less file.txt
# Search for patterns in files
grep &quot;pattern&quot; file.txt
# Change file permissions
chmod 755 file.txt
# Execute command as superuser
sudo apt-get update
# Display system processes
top
# Display disk usage
df -h
```




#Docker Installation 
```
# Add Docker's official GPG key:
sudo apt-get update
sudo apt-get install ca-certificates curl
sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc
```
# Add the repository to Apt sources:
```
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
  $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update
```
#To install the latest version, run:
```
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
sudo docker run hello-world
```











