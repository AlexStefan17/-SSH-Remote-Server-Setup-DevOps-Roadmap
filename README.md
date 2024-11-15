# SSH-Remote-Server-Setup-DevOps-Roadmap
SSH Remote Server Setup challenge for DevOps Roadmap
https://roadmap.sh/projects/ssh-remote-server-setup

## Create Instance and add ssh keys
1. Create EC2 instance
2. Create SSH key from EC2 configuration
3. EC2 login
```
chmod 600 ~/Downloads/first-key.pem
ssh -i ~/Downloads/first-key.pem ec2-user@<EC2_IP>
```
3. Create 2nd ssh key locally: 
```
ssh-keygen -t rsa -b 4096 -f ~/.ssh/my-ec2-key
```
4. Add 2nd pub key to EC2 .ssh/authorized_keys
- connect to EC2
```
vim .ssh/authorized_keys
```
- paste 2nd ssh pub key and save

## Create alis

```
vim .ssh/config
```
- paste confguration for 1st ssh and 2nd ssh

```
Host ec2-key1
  HostName <IP> e.g. 1.21.23.41
  User ubuntu          
  IdentityFile Downloads/SSH-key1.pem
  IdentitiesOnly yes
  
  Host ec2-key2
  HostName <IP> e.g. 1.21.23.41
  User ubuntu          
  IdentityFile ~/.ssh/aws-key-2
  IdentitiesOnly yes
  ```

## Install fail2ban and configure
```
sudo apt install fail2ban -y
sudo cp /etc/fail2ban/jail.conf /etc/fail2ban/jail.local
```
- configure
```
vim /etc/fail2ban/jail.local
sudo systemctl start fail2ban
sudo systemctl enable fail2ban
sudo systemctl status fail2ban
```
