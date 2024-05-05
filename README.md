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
#Add the repository to Apt sources:
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



#check to see if docker is running or not.
```
1) sudo systemctl status docker

# to create container we need image. To right away use
#hub.docker.com - provieds us images not mandatory to download.
# there are number of pre created images to download. 

docker image = base os + application related files

redis is small lightweight database

if create a container using redis image, redis up and runniing 

# we will use apacheweb server httpd
#Apache Httpd is basically a web server used for handling requests and delivering #static content.
#docker image pull imagename
#docker image pull httpd

docekr image has two things 

imagename:image version 

httpd:2.4
httpd:2.2

when you create image you need create like this 

when you dont know name append latest

2) docker image pull httpd:latest

not enough permission 

#run this command
#sudo usermod -aG docker your-user

3) sudo usermod -aG docker ubuntu
#restat putty

4) docker image pull httpd:latest
docker image is pulled, how to check it 

5) docke image ls
#image need to be on local machine 

# to check existing container
6) docker container ls


# to create contaier 
docker container run -d -p 10001:80 --name apache-1 imagename:version
# -d is to tell it to run in background , ex: notepad
# -p is for networking, port tunneling, we will expose  10001 to 80 

7) docker container run -d -p 10001:80 --name apache-1 httpd:latest
#new container is created 

8) docker container ls
every container has unique id and uniqie name 

now apacheweb server is up and running 

let go and access it 
what is the port for outside world?
go to aws and find host ip 

9)on browser- http://hostip:port

```





