# Docker WebUI V.1

### Aim : To create a WebUI such that it can run Docker commands and display the results on the same page.

1. Create a HTML file and CGI program for out WebUI
- Create and Launch a EC2 Instance on AWS

- Transfer the Created files to the EC2 instance 

- Install Apache webserver and Docker
  
  ```bash
  sudo yum install httpd 
  ```
  
  ```bash
  sudo yum install docker
  ```
2. Copy the HTML and CGI program file to /html and /cgi-bin respectively
   
   ```bash
   sudo cp (html_file) /var/www/html
   sudo cp (cgi-prgm_) /var/www/cgi-bin
   ```
- Login with root user
  
  ```bash
  sudo su root
  ```

- Now open the HTML file and replace the IP address with the EC2 Instance Public DNS IP and save it

- Go to cgi-bin folder and make the cgi program file executable.
  
  ```bash
  chmod +x (cgi_prgm_)
  ```
3. Now edit the Sudoers file and the following lines bellow the root
   
   > apache    ALL=(ALL)    NOPASSWD:ALL
- This will allow the WebUI to run the root commands
  
  ```bash
  setenforce 0
  ```

- If firewall blocks the site, then to test it stop the firewall
  
  ```bash
  systemctl stop firewalld
  ```
4. Start and Enable the Docker and httpd services 
   
   ```bash
   systemctl start httpd
   systemctl start docker
   systemctl enable httpd
   systemctl eable docker
   ```

5. Pull an Docker Image to check if Docker is working on the Instance
   
   ```bash
   docker pull centos:latest
   ```

6. Now open the website / type in the Instance Public IP, we can see our Docker WebUI

7. We can use the following Docker commands to test the API
   
   ```bash
   docker images
   docker pull (image_name)
   docker run -it --name (container_name) (image_name)
   docker ps 
   docker stop (container_name)
   docker rm (container_name)
   docker rmi (image_name)
   ```
