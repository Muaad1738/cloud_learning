# Deploying an app

## Launch an EC2 Instance
- Create a new instance using the security group of HTTP, Custom TCP with a port of 3000 and SSH. 

## Create a Nano Script to automate 

```
#!/bin/bash

echo "Updating..."
sudo DEBIAN_FRONTEND=noninteractive apt update -y
echo "Done!"

echo "Upgrading packages..."
sudo DEBIAN_FRONTEND=noninteractive apt upgrade -y
echo "Done!"

echo "Installing Nginx..."
sudo apt install nginx -y
echo "Done!"

# Configure reverse proxy
# Change configuration file

echo "Restarting Nginx..."
sudo systemctl restart nginx
echo "Done!"

echo "Enabling Nginx..."
sudo systemctl enable nginx
echo "Nginx enabled and started on boot."

# Install Node.js version 20.x
echo "Installing Node.js..."
curl -fsSL https://deb.nodesource.com/setup_20.x | sudo -E bash -
sudo apt-get install -y nodejs
echo "Node.js installed!"

# Check Node.js version
node -v

# get the app folder with the app code inside

scp -i "C:\Users\abdul\.ssh\tech258.pem" -r "C:\Users\abdul\app_folder\Sparta_test_folder\app" ubuntu@54.216.176.251:/home/ubuntu

replace the public id with the one on your instance page. 


# cd app folder

locate the app folder

# run app
npm install 
npm start

go to your public ip and add :3000 to access the port 

```



