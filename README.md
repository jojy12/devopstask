# devopstask
# Task2 Docker
# I.Create a custom bridge network with name mynet
>sudo docker network ls
>sudo docker network create mynet
>brctl show
# II.Create two containers with alpine image
sudo docker run -itd --network mynet --name alpinecontainer1 alpine ash
sudo docker run -itd --network mynet --name alpinecontainer2 alpine ash
sudo docker ps
sudo docker network inspect mynet
# III. Ping containers using hostname
sudo docker exec -it alpinecontainer1 ash
ping alpinecontainer2
sudo docker exec -it alpinecontaine2 ash
ping alpinecontainer1
