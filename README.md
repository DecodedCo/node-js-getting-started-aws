# node-js-getting-started

A barebones Node.js app using [Express 4](http://expressjs.com/).

This application supports the [Getting Started with Node on Heroku](https://devcenter.heroku.com/articles/getting-started-with-nodejs) article - check it out.

## Running Locally

Make sure you have [Node.js](http://nodejs.org/) and the [Heroku CLI](https://cli.heroku.com/) installed.

```sh
$ git clone https://github.com/DecodedCo/node-js-getting-started # or clone your own fork
$ cd node-js-getting-started
$ npm install
$ npm start
```

Your app should now be running on [localhost:5000](http://localhost:5000/).

# Deploying to AWS

#### Setup EC2 Instance in AWS Console

1. Log into [AWS Management Console](https://console.aws.amazon.com)
2. Go to the EC2 Management console. Click Services, and choose EC2 under Compute
3. Launch a new instance by clicking the blue “Launch Instance” button
4. Select Amazon Linux 2 (likely defaults to first option)
5. Choose t2.micro type machine
6. Skip to **6. Configure Security Group** and create a security group that allows each of the following types of connections. These will allow us to connect to the instance directly from our own machines, and through a web browser or Dialogflow. See below for the specific settings:

![alt text](https://presley-assets.decoded.com/71271f08-4007-4d92-a14c-e308ba781246_awssetup.png "AWS Setup")

7. Click Review and Launch, then Launch. You’ll be prompted to add a key pair - name a new one and **be sure to download the file** (it will warn you if you don’t click download).

8. Launch the instance and edit the name to something memorable (double-click on the name field)

#### Setup EC2 Instance from Terminal

9. Move the .pem keyfile you downloaded to this project directory. In a Terminal, navigate to this directory (`$ cd node-js-getting-started-aws`) and run `$ chmod 400 <filename>` to set appropriate file permissions.

10. Edit config.json to include the filename of the keyfile, the EC2 username (by default for the Amazon Linux option we picked, it’s ec2-user) and the public DNS of your instance from the EC2 console. Save the file.

11. In a Terminal, run `$ node setup` from the project directory to install node and download the necessary packages to run the webapp. It may prompt you to accept the ECDSA signature - simply type “yes” and rerun `$ node setup`.


#### Deploy App to Instance

Once you have completed all of the setup steps, you should be ready to deploy your app!

1. In a Terminal, run `$ node deploy` from the project directory.

2. Navigate to the IP address printed out, or get the public IP from the EC2 page on the AWS console

3. Visit public IP on port 5000 (example, 12.345.6.78:5000) in the browser and see your app!

