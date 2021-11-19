# DevOpsTask
# Task 1 AWS
# Create the target group with two AWS instances with the Ubuntu operating system
i.Open the AWS console.Goto service.Go to EC2.Launch 2 separate Instances-Webserver1 and Webserver2 with Ubuntu 20.04 AMI Image,Instance type t2.micro,Instance Details,Add storage Add EBS,Createor add security group with ssh and http inbound rules and Create keypair generates .pem key. <br/>
$  ssh ubuntu@ipaddress - SSH into Webserver1<br/>
$ sudo apt update //update the repository<br/>
$ sudo apt-get install nginx -y //Install nginx<br/>
$ sudo service nginx status //check status of nginx as running<br/>
$ cd /var/www/html<br/>
$ sudo rm present html file<br/>
$ sudo nano index1.html<br/>
$ copy paste the source code of provided html page and save and exit the editor<br/>
$ sudo nano /etc/nginx/sites-available/default //changing the index to point to index.html file<br/>
$ sudo ln -s /etc/nginx/sites-available/default /etc/nginx/sites-enabled/  //this creates a link to the configuration file<br/>
$ sudo nginx -t //checking the syntax<br/>
$ sudo service nginx restart<br/>

Repeating the same steps of webserver configuration in Webserver2 with source code of index2.html<br/>
Checking http://webserver1ipaddress/index1.html<br/>
Checking http://webserver2ipaddress/index2.html<br/>

# Creating Load Balancer - webserverLB
Create Target Group named targetgroup1.<br/>
Add webserver1 and webserver 2 to the target group.Attach target group to the webserverLB<br/>
Check with DNS address of the Load Balancer<br/>

# devopstask
# Task2 Docker
# I.Create a custom bridge network with name mynet
*sudo docker network ls<br/>
*sudo docker network create mynet<br/>
*brctl show<br/>
# II.Create two containers with alpine image
*sudo docker run -itd --network mynet --name alpinecontainer1 alpine ash<br/>
*sudo docker run -itd --network mynet --name alpinecontainer2 alpine ash<br/>
*sudo docker ps<br/>
*sudo docker network inspect mynet<br/>
# III. Ping containers using hostname
*sudo docker exec -it alpinecontainer1 ash<br/>
*ping alpinecontainer2<br/>
*sudo docker exec -it alpinecontainer2 ash<br/>
*ping alpinecontainer1<br/>
