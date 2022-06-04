# How to Install Jenkins,Git,Docker on Amazon EC2 Instance

In this part, I will show how to install and launch Jenkins,Git,Docker on a AWS EC2 instance.

Let's get start with Jenkins

## Installing Jenkins

- Create Ubuntu 18.04 EC2 Instance.
Once you logged in to your AWS account and accessed your Ubuntu Server 18.04 LTS instance you can follow the below steps to install Jenkins.

- Update Ubuntu Server
Before installing Jenkins you have to update software packages on Ubuntu server for that use below commands.
```console
sudo apt-get update -y
```

- Add Repository Key
You have to add Jenkins repository into Ubuntu server.
```console
wget -q -O - https://pkg.jenkins.io/debian-stable/jenkins.io.key | sudo apt-key add -
```
<img width="678" alt="Ekran Resmi 2022-06-01 22 42 56" src="https://user-images.githubusercontent.com/91700155/171916422-50e0881f-52db-4c3f-8209-a96600f5e9af.png">

- Add Package Repository
```console
sudo sh -c 'echo deb http://pkg.jenkins.io/debian-stable binary/ > /etc/apt/sources.list.d/jenkins.list'
```
<img width="673" alt="Ekran Resmi 2022-06-01 22 43 14" src="https://user-images.githubusercontent.com/91700155/171916448-6b59b55d-6d38-4c61-bfca-30da0695e1ed.png">

- Now, to update the server
```console
sudo apt update
```

- Install Jenkins Dependencies
We first have to install java
```console
sudo apt install default-jre -y
```
<img width="675" alt="Ekran Resmi 2022-06-01 22 45 44" src="https://user-images.githubusercontent.com/91700155/171916810-22ceaf5f-ea20-463c-b67e-79980cb6a161.png">

```console
sudo apt install jenkins -y
```
<img width="674" alt="Ekran Resmi 2022-06-01 22 52 13" src="https://user-images.githubusercontent.com/91700155/171917039-8fd56d35-b52e-490f-a1ea-908aae3be939.png">

And Jenkins installation completed you have to start Jenkins service
```console
sudo systemctl start jenkins
sudo systemctl status jenkins
```
<img width="674" alt="Ekran Resmi 2022-06-01 22 54 48" src="https://user-images.githubusercontent.com/91700155/171917298-b3ef75a5-4a2b-416f-87fb-51ea1dcf4384.png">

- Allow Jenkins Port On Ubuntu Firewall
By default Ubuntu server has firewall installed and we have to allow Jenkins port 8080 from firewall so that we can access Jenkins.
```console
sudo ufw allow 8080
```
<img width="730" alt="Ekran Resmi 2022-06-01 22 56 40" src="https://user-images.githubusercontent.com/91700155/171917803-ac3c1d77-ed7c-4bb7-98c2-49266c1c8537.png">

If the Ubuntu machine firewall is not enabled, you can use the commands below to check it.
```console
sudo ufw status
```
If your Ubuntu firewall is inactive use
```console
sudo ufw allow OpenSSH sudo ufw enable
sudo ufw enable
sudo ufw status
```
<img width="729" alt="Ekran Resmi 2022-06-01 22 58 23" src="https://user-images.githubusercontent.com/91700155/171917743-df49d1fb-4fd2-403a-9a6f-aa8cf84d4270.png">
<img width="732" alt="Ekran Resmi 2022-06-01 22 58 45" src="https://user-images.githubusercontent.com/91700155/171917762-a06d4de1-2e04-486d-991f-db9cd70781e6.png">

- Setting Up Your Jenkins
Now to access Jenkins from web browser you must also allow Jenkins port 8080 in AWS security group and after that you will be able to access Jenkins. So go to your AWS account-Security group and add port 8080.

- As a last part, pen web browser and type your AWS Ec2 Ubuntu instance public IP address with 8080 port.
<img width="921" alt="Ekran Resmi 2022-06-01 22 59 47" src="https://user-images.githubusercontent.com/91700155/171918011-da815e10-f55d-4702-b542-3b760a065d80.png">

- As per the instructions in the screenshot above, you need to get the default admin password from the given path, so on your Ubuntu machine you would issue the following command to get it.
```console
sudo cat /var/lib/jenkins/secrets/initialAdminPassword
```
<img width="731" alt="Ekran Resmi 2022-06-01 23 00 12" src="https://user-images.githubusercontent.com/91700155/171918046-9d7a8ad4-2cdd-4a1f-9e61-ad481a8637a3.png">

- You will get the following output and this is the default admin password to login to Jenkins copy this and use it in web browser for Jenkins login.

- When you login to Jenkins with default admin password, it will present two options and this is recommended plugins and choose plugins to install. We recommend clicking on the suggested plugins and jenkins will take care of the plugin installations.

<img width="845" alt="Ekran Resmi 2022-06-01 23 01 04" src="https://user-images.githubusercontent.com/91700155/171918390-a3884ea8-45db-442b-8786-880890b587b8.png">

- The plugins will take some time to install and once all plugins are installed Jenkins will ask you to create your Admin user account. Next, fill in your desired admin user details and set Jenkins admin credentials.

<img width="850" alt="Ekran Resmi 2022-06-01 23 05 39" src="https://user-images.githubusercontent.com/91700155/171918448-9a702301-eb36-46cd-a9bd-f6d98560552f.png">

- Click Save and Finish after setting your Jenkins access url and other information. Finally you will get a confirmation page and it will be "Jenkins Ready".
- 
<img width="843" alt="Ekran Resmi 2022-06-01 23 06 51" src="https://user-images.githubusercontent.com/91700155/171918700-64ff1eaf-23f8-40c7-98dd-a8113ef1c410.png">

![Ekran Resmi 2022-06-03 20 48 44](https://user-images.githubusercontent.com/91700155/171918889-0dd81b24-834d-4697-892a-9fd2c593ff88.png)

<p> </br>
  
## Installing Git

- Update Ubuntu Server
Before installing Git you have to update software packages on Ubuntu server for that use below commands.
```console
sudo apt-get update -y
```

- Install Jenkins Dependencies
```console
sudo apt install git -y
git --version
```
<img width="479" alt="Ekran Resmi 2022-06-02 18 45 03" src="https://user-images.githubusercontent.com/91700155/171920672-30d0da0b-5989-4fa9-8796-8a7420641ea5.png">

<img width="355" alt="Ekran Resmi 2022-06-02 18 45 11" src="https://user-images.githubusercontent.com/91700155/171920736-1361c550-6cb1-4704-b73d-cc8ee8ed9f16.png">


## What’s Docker?
Docker is an open platform for developers and sysadmins to build, ship, and run distributed applications.

## Installing Docker
Running Docker on AWS provides administrators and developers a highly reliable, cost-effective way to build, ship, and run distributed applications. Docker can be installed on many different operating systems, including Linux distributions like Ubuntu and even Mac OSX and Windows.

```console
sudo apt-get update
```

```console
sudo apt install docker.io
```
<img width="831" alt="Ekran Resmi 2022-06-02 18 45 41" src="https://user-images.githubusercontent.com/91700155/171920935-322694e9-9b11-4337-a639-12ba3bec5c0d.png">

```console
service docker.io start
service docker.io status
```

- Basic Commands for Docker
```console
sudo docker info
```
<img width="773" alt="Ekran Resmi 2022-06-02 18 46 27" src="https://user-images.githubusercontent.com/91700155/171923073-91265d33-c84f-461f-8bab-1185ddb1dd09.png">

```console
sudo docker images
sudo docker ps
```
<img width="684" alt="Ekran Resmi 2022-06-02 18 46 40" src="https://user-images.githubusercontent.com/91700155/171923136-31628700-4a5f-499c-98ba-e5c3dee4d9ca.png">

- Run Docker Image:
By default, docker pulls the images from a Docker registry called Docker Hub managed by Docker company.
To confirm whether you can download the images from Docker Hub:

```console
sudo docker run hello-world
```
<img width="773" alt="Ekran Resmi 2022-06-02 18 47 25" src="https://user-images.githubusercontent.com/91700155/171923275-b59b2d22-58ca-4c95-9e01-a15cdeeaa8b4.png">

