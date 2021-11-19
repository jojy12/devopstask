# DevOpsTask
# Task 1 AWS
# Create the target group with two AWS instances with the Ubuntu operating system
i.Open the AWS console.Goto service.Go to EC2.Launch 2 separate Instances-Webserver1 and Webserver2 with Ubuntu 20.04 AMI Image,Instance type t2.micro,Instance Details,Add storage Add EBS,Createor add security group with ssh and http inbound rules and Create keypair generates .pem key. 
$  ssh ubuntu@ipaddress - SSH into Webserver1
$ sudo apt update //update the repository
$ sudo apt-get install nginx -y //Install nginx
$ sudo service nginx status //check status of nginx as running
$ cd /var/www/html
$ sudo rm present html file
$ sudo nano index1.html
$ copy paste the source code of provided html page and save and exit the editor
$ sudo nano /etc/nginx/sites-available/default //changing the index to point to index.html file
$ sudo ln -s /etc/nginx/sites-available/default /etc/nginx/sites-enabled/  //this creates a link to the configuration file
$ sudo nginx -t //checking the syntax
$ sudo service nginx restart

Repeating the same steps of webserver configuration in Webserver2 with source code of index2.html
Checking http://webserver1ipaddress/index1.html
Checking http://webserver2ipaddress/index2.html

# Creating Load Balancer - webserverLB
Create Target Group named targetgroup1.Add webserver1 and webserver 2 to the target group.Attach target group to the webserverLB
Check with DNS address of the Load Balancer

# devopstask
# Task2 Docker
# I.Create a custom bridge network with name mynet
*sudo docker network ls
*sudo docker network create mynet
*brctl show
# II.Create two containers with alpine image
*sudo docker run -itd --network mynet --name alpinecontainer1 alpine ash
*sudo docker run -itd --network mynet --name alpinecontainer2 alpine ash
*sudo docker ps
*sudo docker network inspect mynet
# III. Ping containers using hostname
*sudo docker exec -it alpinecontainer1 ash
*ping alpinecontainer2
*sudo docker exec -it alpinecontainer2 ash
*ping alpinecontainer1
