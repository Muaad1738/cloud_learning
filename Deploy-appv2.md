# Deploying an App

## Launch Instance 

- Create a new instance using the security group of HTTP, Custom TCP with a port of 3000 and SSH.

## Update
```bash
sudo DEBIAN_FRONTEND=noninteractive apt update -y
```

## Upgrade
```bash
sudo DEBIAN_FRONTEND=noninteractive apt upgrade -y
```

## Install
```bash
sudo apt install nginx -y
```
## Configure reverse proxy
```bash
sudo nano /etc/nginx/sites-enabled/default
```
- Change "try_files $uri $uri/ =404;" to proxy_pass http://localhost:3000;
- restart Nginx

## Restart

```bash
sudo systemctl restart nginx
```

## Enable

```bash
sudo systemctl enable nginx
```

## Install Node
```bash
curl -fsSL https://deb.nodesource.com/setup_20.x | sudo DEBIAN_FRONTEND=noninteractive -E bash - && sudo DEBIAN_FRONTEND=noninteractive apt-get install -y nodejs
```
## Clone
```bash
git clone https://github.com/Muaad1738/tech258-sparta-test-app.git
```

## Check Node Version

```bash
node -v
```

## Navigate to the App Folder
```bash
cd ~/tech258-sparta-test-app/sparta_test_folder/app
```
## set db host env var
```bash
export DB_HOST=mongodb://172.31.63.98:27017/posts
```
- Make sure you use the private ip on the database intance you launched.
  
## Install the App
```bash
npm install
```
## Run the App

```bash
sudo npm start
```
## Test each stage

Do it manually and test each stage to make sure its wokring correctly then automate the process using a nano script

## Nano script 

``` bash
#!/bin/bash

echo "Updating..."
sudo apt update -y
echo "Done!"

echo "Upgrading packages..."
sudo DEBIAN_FRONTEND=noninteractive apt upgrade -y
echo "Done!"

echo "Installing Nginx..."
sudo DEBIAN_FRONTEND=noninteractive apt install nginx -y
echo "Done!"

# Configure reverse proxy
sudo sed -i '51s/.*/\t  proxy_pass http:\/\/localhost:3000;/' /etc/nginx/sites-enabled/default

# Change configuration file

echo "Restarting Nginx..."
sudo systemctl restart nginx
echo "Done!"ls

echo "Enabling Nginx..."
sudo systemctl enable nginx
echo "Nginx enabled and started on boot."

# Install Node.js version 20.x
echo "Installing Node.js..."
curl -fsSL https://deb.nodesource.com/setup_20.x | sudo DEBIAN_FRONTEND=noninteractive -E bash - && sudo DEBIAN_FRONTEND=noninteractive apt-get install -y nodejs
echo "Node.js installed!"

# Check Node.js version
echo "Node.js version:"
node -v

# Clone the Git repository
echo "Cloning the Git repository..."
git clone https://github.com/Muaad1738/tech258-sparta-test-app.git ~/tech258-sparta-test-app
echo "Git repository cloned!"

# Navigate to the app folder
echo "Navigating to the app folder..."
cd ~/tech258-sparta-test-app/Sparta_test_folder/app


# set db host env var
export DB_HOST=mongodb://172.31.63.98:27017/posts

# Install app dependencies
echo "Installing app dependencies..."
npm install
echo "App dependencies installed!"

# Install PM2
echo "Installing PM2..."
sudo npm install -g pm2
echo "PM2 installed"


# run the app
#echo "Running the app with PM2..."
pm2 start app.js
echo "App started with PM2!"




```
# Deploying a Database 

## Launch Instance 

- Create a new instance using the security group of Custom TCP with a port of 27017 and SSH

## Update

``` bash
sudo apt update -y
```

## Upgrade
```bash
sudo DEBIAN_FRONTEND=noninteractive apt upgrade -y
```
## Install MongoDB

```bash
curl -fsSL https://www.mongodb.org/static/pgp/server-7.0.asc | \
   sudo gpg -o /usr/share/keyrings/mongodb-server-7.0.gpg \
   --dearmor
```
```bash
echo "deb [ arch=amd64,arm64 signed-by=/usr/share/keyrings/mongodb-server-7.0.gpg ] https://repo.mongodb.org/apt/ubuntu jammy/mongodb-org/7.0 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-7.0.list
```
```bash
sudo apt-get update 
```
```bash
sudo DEBIAN_FRONTEND=noninteractive apt-get install -y mongodb-org=7.0.6 mongodb-org-database=7.0.6 mongodb-org-server=7.0.6 mongodb-mongosh=2.2.4 mongodb-org-mongos=7.0.6 mongodb-org-tools=7.0.6

``` 



## Configure Bind IP in MongoDB Config File 
```bash
sudo nano /etc/mongod.conf
```
- Change the values to 0.0.0.0 

## Restart MongoDB
```bash
sudo systemctl restart mongod
```
## Enable MongoDB
``` bash
sudo systemctl enable mongod
```

## Nano Script 

```bash
#!/bin/bash
# config needrestart.config
# non interactive into command which install things

# Update
echo Updating...
sudo apt update -y
echo Done!

# Upgrade
echo Upgrading packages...
sudo DEBIAN_FRONTEND=noninteractive apt upgrade -y
echo Done!

# Install MongoDB 7.0.6
echo Installing MongoDB 7.0.6...
curl -fsSL https://www.mongodb.org/static/pgp/server-7.0.asc | \
   sudo gpg -o /usr/share/keyrings/mongodb-server-7.0.gpg \
   --dearmor

echo "deb [ arch=amd64,arm64 signed-by=/usr/share/keyrings/mongodb-server-7.0.gpg ] https://repo.mongodb.org/apt/ubuntu jammy/mongodb-org/7.0 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-7.0.list

sudo apt-get update 

sudo DEBIAN_FRONTEND=noninteractive apt-get install -y mongodb-org=7.0.6 mongodb-org-database=7.0.6 mongodb-org-server=7.0.6 mongodb-mongosh=2.2.4 mongodb-org-mongos=7.0.6 mongodb-org-tools=7.0.6


# Configure bind IP in MongoDB config file
echo Configuring MongoDB...
sudo sed -i 's/bindIp: 127.0.0.1/bindIp: 0.0.0.0/' /etc/mongod.conf

# Restart MongoDB
echo Restarting MongoDB...
sudo systemctl restart mongod

# Enable MongoDB
echo Enabling MongoDB...
sudo systemctl enable mongod
```
## Blockers

- Reflecting on my journey, I've faced several blockers that taught me valuable lessons. Running the app before configuring the database led to unexpected errors,such as my database not connecting. Using the wrong IP for the database host resulted in connection issues, emphasising the need for attention to detail. Not using sudo when installing PM2 led to permission denied errors, highlighting the importance of system permissions.

    Majority of these issues were simple fixes but it highlighted the need to be through and not rush through in installing the app and connecting the database.







