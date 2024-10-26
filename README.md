# E-Commerce Platform Deployment with Git, Linux and AWS
### The following steps are taken to deploy this project

## Steps: Initialize Git Repository
Begin by creating a project directory named **"MarketPeak_Ecommerce"**
Inside this directory, intialize a Git repo to manage version control.
```mkdir MarketPeak_Ecommerce
cd MarketPeak_Ecommerce
git init
```
![](./Img/01.png)

## Obtain and Prepare the E-Commerce Website Templete
Instead of building the website from scratch, we are using a pre-existing ecommerce template.
The website has been imported into the **"MarketPeak_Ecommerce"** directory.
run the code ```ls``` to view the content of the directory. Here the template has been successfully imported.
![](./Img/02.png)

## Stage and Commit The Template to Git

Add the website files to the Git Repo
Set Git global configuration with username and email
Commit these changes with a clear, descriptive Message.
![](./Img/03.png)

### Push the code to Github Repository
After initializing Git repo and adding the e-commerce template, next step is to push the code to a remote repository on Github. 
Follow these **steps**
- Create a Remote Repository on Github, name it **"MarketPeak_Ecommerce**
![](./Img/03i.png)
- Link Your Local Repository to Github within your project directory. 
```
git remote add origin https://github.com/your-git-username/MarketPeak_Ecommerce.git
```
- Push Your Code: Upload the local repo content to GitHub.
```
git push -u origin main
```
![](./Img/04.png)

# AWS DEPLOYMENT

To deploy **"MarketPeak_Ecommerce"** platform, start by setting up Amazon EC2 instance:

- Log in to the AWS Management Console
- Launch an EC2 instance using an Amazon Linux AMI
- Set the Security Group to allow HTTP connection from any IP
- Connect to the instance using SSH
![](./Img/05i.png)
![](./Img/05ii.png)

### Amazon Ec2 Instance has been launched
![](./Img/06.png)

- Change to the **root** user, this gives you ```sudo``` privileges
![](./Img/07.png)

# Install Web Server on EC2
We are using **Apache** HTTP Server (httpd), this is a widely used web server that serves HTML files and contents over the internet. 

- Install Apache web server on the Ec2 instance, Note: httpd is the software name for Apache on systems using the yum package manager

```
sudo yum update -y
sudo yum install httpd -y
sudo systemctl start httpd
sudo systemctl enable httpd
```
![](./Img/08.png)

```cd``` into the apache server that has been installed

```cd /var/www/html```

install git with the code ```yum install git -y```
![](./Img/09.png)

Use the **https** clone URL to clone the repository
```ls``` to view if successfully done.
![](./Img/10.png)

``cd`` into the cloned directory
![](./Img/11.png)
Now, we have to move the file contents to the document root (httpd)
run the command ``` mv * .. ```

- change directory back to ***document root** which is apache httpd
- ```ls``` to view the moved content
![](./Img/12.png)

- reload the web server  ```sudo systemctl reload httpd```.

## Now its time to test the Job done so far.
- With ***httpd*** configured and website files in place, **MarketPeak_Ecommerce** platform is now live on the internet!!!

- Locate the public ip of your Web Server, Open a Web browser to view the deployed website.
![](./Img/13.png)

![](./Img/14.png)
