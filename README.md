# Git Commands

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

# Linux Commands 
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

# Kuberbetes 

creating first pod
------------------------
```
#check any existing pods 
1) kubectl get pods
no resources found - resource here it means pod


#to deploy 
2)kubectl apply -f pod.yaml

#to check 0/1 ? 1/1 ? 
3) kubectl get pods 

to get more informatin, where it got deployed?. 
every pod has ip address, using which pods can communicate. 
4) kubectl get pods -o wide

5) kubectl get nodes
cheeck to see on which node it is created. Kubernetes takes this decison on which node it 

#how to delete a pod ## we cannot stop a pod only delete 
6) kubectl delete pod sample-pod

#to check..
7) kubectl get pods


---------------------------
This basic object it dosent have all the featues , selfhealing, auto recovery
---------------------------

Next---
----------------

replicaset is object which is foundation of kubernetes and has all 

feature of K


replicate
auto scale-in
auto scale-out
self healing

"K will give you freedom from datacenter"
"Docekr will give freedom from host os"



#now the kind is replicaset, it keeps changing. 
#metadata -sales-app 
# 1applicaiton(sales/web/backend) - 1 replicaset
#specificaiton  number of replcias we want to create 
# we need to specify one
#earlier we managed pods : now replciaset objeict, it will manage the pods.
#it will constantly check(here its is 4pods )  and maintain that state
# every replca will have same name : lable name . match lable 

# then we defince resources

#To deploy
8) kubectl apply -f replicaSet.yaml

to get information control plane:  desired , current, ready
9) kubectl get replicaset

what are createdkube
10) kubectl get pods

#to see where it is created 
11) kubectl get pods -o wide 

#To check nodes
12) kubectl get nodes

pods get deployed on worker, when there is no
space it will tell no space on worker. 

---------------------------------------------

Now we will see auto scale in
------------------------------------------------

now we have more traffic and four pods are not enough
- due to more festival offer

solution ? increase the number of pods. To share load. to respond quicly. 
 

We will go to my replicaset and change from 4 to 6

13) kubectl apply -f replicaSet.yaml
#observe:
"first time it will tell created"
apply agian it will tell configured 


14) kubectl get replicaset
observer:this is called auto scale-in creating new pods without
disturbing existing pods

-----------auto sale out ----------

now traffic is less we dont need that many pods 

we can reduce go and change pods form 6 to 5

15) kubectl apply -f replicaSet.yaml

16) kubectl get replicaset

#obsever new pods are created without disturbing the exisiting : autoscale in - scaling up. 

#to see where it is created 
17) kubectl get pods -o wide 


youngest pods will be deleted. Oldest one will stay.


-----------selfhealing---famous feature of kubernetes------
if someone unknowling delted pod

5 pods is the desired state, K will ensure that it maintained

#to delete a pod (object type and object name)
17) kubectl delete pod pod_name
vi
#to chekc
18) kubectl get pods -o wide 
new pod will be created

-----------------------------------
can try deleteing two pods

19) kubectl delete pod pod1 pod2

#to chekc
20) kubectl get pods -o wide 
new pod will be created
-----------------------------------

now to permanetnlty delete a pod 


21) kubectl delete -f replicate.yaml 


22) kubectl get pods
all pods will terminate
```

#  Docker Installation 
```
# Add Docker's official GPG key:
sudo apt-get update
sudo apt-get install ca-certificates curl
sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc
```
#  Add the repository to Apt sources:
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

#dockerfilecreation 

```
#ensure there is seperate directory for docker file.
#input file name should be dockerfile only.
#cant have two file in same locaiton 


#create folder 
1) mkdir webapp

2) cd webapp
place allthe assests related to that applicaiton in here

3a) vi index.html

<html> <body> <h1> 
docker created by : type your ROll number 
</h1></body><html>


3b)vi Dockerfile

#docker file can have comment lines with # and space

----------------------------------------------------------------
#This is docker file for apache sever

#Remember first valid line should be FROM

FROM ubuntu:12.04

MAINTAINER yourname <yourname@gmail.com>

LABEL appname="customercare"\
      appversion="1.0.0"

#this application related logic - under this user and group i want to run apcache 
#and store log file in that location

ENV APACHE_RUN_USER www-data
ENV APACHE_RUN_GROUP www-data
ENV APACHE_LOG_DIR /var/log/apache2

#install apache

RUN apt-get update
RUN apt-get install -y apache2
RUn apt-get clean

# deploy some code- 
#following is the static location where index.html should be placed
#we need to create index.html in local machine
#ADD command has additional capability 
#here we are using COPY

COPY index.html /var/www/

#we can use ADD command too
# it can handle .zip files 

# for 80 - tcp  by default --for udp you need mention with 55/udp
# every software has default port
#enterprice has complete control on which port to run.

EXPOSE 80

CMD ["/usr/sbin/apache2", "-D", "FOREGROUND"]
```

linking containers:
For two container to talk to each other -
its legacy feature


```
1) docker container ls

remove any existing containers

2) docker container run -d -p 24000:80 --name apache-2 httpd:latest

3) docker container run -d -p 25000:80 --name apache-3 --link apache-2 httpd:latest

how to verify ?

go inside the container

4) docker container exec -it apache-3 /bin/bash

5)hostname

6) ping apache-2

7) apt-get update > /dev/null

8) apt-get install -y iputils-ping >/dev/null


9) ping apache-2

----------------end of linking containers-------
```

---------------------------------
docker volumes
-----------------------------------


```
# this standard and prefereed

# docker volume is created and handled by docker itself

# in case of bind mount we had complete freedom to load from which ever location
we in local OS

#docker volume is going to mount from specific location 

37) cd /var/lib/docker/

38) sudo ls -l

# inside the volumes directory, 
this is location you need to mount to container

-----------------------
how to create volume 
-----------------------

39) docker volume ls

no volumes 

40) docker volume create websitedata
# created volume

41)docker volume ls 

this volume is in specific location , how to find out 

42) docker volume inspect websitedata

this is pointing to locaiton /var/lib/docker/volumes/ ...


43) sudo ls /var/lib/docker/volumes/

this is where you data gets stored. 


44) now how to mount volume

swithc to sudo as we need lot of root access
45) sudo su -

46) docker container run -d -p 23000:80 -v websitedata:/usr/local/apache2/htdocs --name apache-3 httpd:latest

#since it is native location no need to give entire locaation 

47) docker container ls

now lets go to the location and chekc if there is anydata

48) cd /var/lib/docker/volumes/websitedata_data

49) ls 

from where did it index.html come

when mounting empty volume , container data will be stored
in local volume 

now let us login inside the container 

50) docker container exec -it apache-3 /bin/bash

51)ls
52)cd htdocs
53) echo "welcome to docker" > sample.txt

54) exit 

55)pwd

56) ls 

now delete contaier 
57) docker continer rm -f apache-3
```

#dockercompose 

install docker compose 

its does not come by default.


```
1) sudo su -

2) sudo curl -L "https://github.com/docker/compose/releases/download/1.26.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose

verify in the following

3)  ls -l /usr/local/bin/

its a binary file it needs executable permission. 

4) chmod +x /usr/local/bin/docker-compose

5) echo $PATH
we can store docker in anyone of the following bin

6) docker-compose --version

7) docker version 

observer the difference in versions 

-------------------------------------------------
```





---------------------------------
# docker-compoes activity :
```
1 Create a sample python program 
2 Containerize it 
3 upload the image to docker hub
# the command we run on command line: contaier run -d -p.
4 create a compose YAML file to declare docker configuration 
5 Add database config


8) cd /opt/
9) mkdir PythonApp
10 cd PythonApp
11) vi app.py
12) vi Dockerfile 


# alpine is general purpose linux os
# its a python based image 
#alpine images are lightweight image 
#its more secure os : since it has less features
# it has minimal feature it take 200mb space on disk
# alpine image is 5mb 

From python:3.7-alpine

#workdir is to change from one location to another. 
#move to code directory inside ,it like cd inside
WORKDIR /code

# flask is a python module, like in java -hibrnate, spring

ENV FLASK_APP app.py
ENV FLASK_RUN_HOST 0.0.0.0

#command to install in appine is apk 
#prerequists are installed here

RUN apk add --no-cache gcc musl-dev linux-headers

COPY requirements.txt requirements.txt

RUN pip install -r requirements.txt

EXPOSE 5000

COPY . . 

CMD ["flask","run"]

---------------------------------------------

#now we need to make file with requirments.txt file 


13) vi requirements.txt 

now we can run the command .. docker container run ... 




# create docker image using Dcoker file
13.1 docker image build -t myapache:1.0.0 .



14) vi docker-compose.yaml

#we have defined two services 
#web servies
#redis service 

#for webservice we are giving . (docker file as as input 
and create container out of it)

#for redis we are giving redis image as input.

version: '3'
services: 
  web:
     build: .
     ports:
       - "5000:5000"
   redis:
     image: "redis:alpine"

15)docker-compose 
see possibe options

16)docker-compose ps
lists the running containers

docker-compose config -q
before creating container 

17) docker-compose up -d
#up is used for creating new contaiers

18) docker-compose stop 
#will stop containers

19)docker-compose ps
#observe if they containers are stoped or not.

20) dokcer-compose start
#start-to start containers

21) docker-compose ps

#to remove 
22)docker-compose down

23) docker-compose ps 


docker-compose stop

```
