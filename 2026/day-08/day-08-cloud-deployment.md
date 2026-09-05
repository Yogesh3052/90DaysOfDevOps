## successfully created EC2
![alt text](image.png)
## SSH connection to your server
![alt text](image-1.png)
## Nginx welcome page accessible from browser
![alt text](image-2.png)
## Log file contents
![alt text](image-3.png)

## commands used
- sudo apt update && apt upgrade
- sudo apt-get install nginx -y
- systemctl status nginx
- scp -i "Nginx server key.pem" ubuntu@16.171.199.217:/home/ubuntu/notes.log .
