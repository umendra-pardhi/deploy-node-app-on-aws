# deploy-node-app-on-aws
Deploy node.js app on AWS (Amazon Web Services)


Before you can deploy your Node.js app, you'll need to connect to your AWS EC2 instance. 

Ensure you have your EC2 instance running.

## Step 1: Switch to Root User & Update Packages

Once connected, you will have access to the command line of your EC2 instance.

To ensure you have the latest software and security updates, switch to the root user and update the package lists by running following commands:

```bash
sudo su
apt update -y
```

## Step 2: Install Node.js and NPM using NVM
### Install NVM
Run the following command to download and install NVM:

```bash
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.1/install.sh | bash
```
### Activate NVM:
Run the following command to activate NVM.

```bash
. ~/.nvm/nvm.sh
```
### Install the Latest LTS Version of Node.js:
Use NVM to install the latest long-term support (LTS) version of Node.js:

```bash
nvm install --lts
```
### Verify Node.js and NPM Installation:
Check that Node.js and NPM are installed correctly:
```bash
node -v
npm -v
```


## Step 3: Install Git and Clone Your Repository

### Install Git:
Install Git with the following command:
```bash
apt install git -y
```
### Verify Git Installation:
Ensure Git is installed and check its version:
```bash
git --version
```

### Clone Your Repository:
Clone your Node.js application repository from GitHub:

```bash
git clone https://github.com/umendra-pardhi/test-node-app.git
```

### Navigate to the Application Directory and Install Dependencies:

```bash
cd test-node-app
npm install
```

### Start the application
Start your Node.js application using NPM:

```bash
npm start
```
## Congratulations! Your Node.js Application is Deployed

### Access Your Application

#### Copy the Public IP Address: 
Go to the AWS Management Console, find your EC2 instance, and copy its public IP address.
#### Open a Web Browser: 
Paste the public IP address into your browser’s address bar (e.g., http://your-ec2-instance-public-ip).
#### Verify: 
You should see the message "Hello from node js server!".
If you see this message, your application is running correctly.

## Step 4: Install and Use PM2 for Process Management
### Install PM2:

Install PM2 globally using NPM:

```bash
npm install pm2 -g
```

### Start Your Application with PM2:

Start your application and assign it a name:

```bash
pm2 start index.js --name "myapp"
```
Replace index.js with the path to your application's main file.


### List All Running Processes/Apps:

View all applications managed by PM2:

```bash
pm2 list   # or alternatively pm2 ls
```


### Manage Your Application with PM2:

Stop an Application:

```bash
pm2 stop <app_name|id|'all'>
```
Restart an Application:
```bash
pm2 restart <app_name|id|'all'>
```
Delete an Application:
```bash
pm2 delete <app_name|id|'all'>
```
Replace <app_name> with your application's name, <id> with the process ID, or use 'all' for all applications.

### View Logs with PM2:

View Logs for All Applications:

```bash
pm2 logs
```
View Logs for a Specific Application:
```bash
pm2 logs <app_name|id>
```


### Monitor Resources with PM2:
Monitor your application's resource usage in real-time:
```bash
pm2 monit
```

### Set Up PM2 to Start on Boot:
Configure PM2 to launch your applications automatically when the server reboots:
```bash
pm2 startup
```
