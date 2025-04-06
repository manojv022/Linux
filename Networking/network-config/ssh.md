 #### Install openssh:
  
- sudo apt update
- sudo apt install openssh-server
- sudo systemctl status ssh
- sudo systemctl enable ssh
- sudo systemctl status sshd


ssh username@your_server_ip

ssh-copy-id username@your_server_ip



##### Configure Firewall's:

- sudo ufw allow ssh
- sudo ufw enable
- sudo ufw status
