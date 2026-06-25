(read about the app itself below)
This is a Terraform deployment via push of node js app.
PROCESS
---
CI from workflow builds, test if container is still running, and pushes to docker hub if it does. 
each push has a unique githab hash tag.
After push, the CI triggers workflow dispatch of this repo: https://github.com/meditator3/trigger_tf_mlm
which grabs the image tag and parses it later on.
the dispatched Terraform repo builds all aws resources - eks, vpc/private/pub subnets/nat/igw, 
including a helm chart custom made which uses the image tag and pulls the current/latest image from dockerhub.
the helm chart has deployment for the app, service and ingress>which builds the alb in return.
at the end of the terraform and the helm deplymend(CD), also terraform triggered, an output of the ip
of the alb is printed in the logs of CD for /etc/hosts routing locally.

this deployment is without ACM and https, because it requires to buy the domain.
in order to see the app itself and the changes:
(in windows)
edit as admin-
windows/system32/drivers/etc/hosts
<ip of alb from tf log> demoapp.com

<img width="3802" height="1957" alt="demoapp-proof" src="https://github.com/user-attachments/assets/09099e74-1072-499f-a616-d5d08bdf9e74" />





















# Node.js Demo Application
Node.js basic application useful for demos and examples

&nbsp;

## General Information

The application show a basic web page
![Welcome-Page](https://github.com/selaworkshops/npm-demo-app/blob/master/Images/Image1.png?raw=true)

The application have a basic function to determine if a number is prime or not
![Welcome-Page](https://github.com/selaworkshops/npm-demo-app/blob/master/Images/Image2.png?raw=true)

The folder “spec” contains the application tests which are run using the jasmine-node module
![Welcome-Page](https://github.com/selaworkshops/npm-demo-app/blob/master/Images/Image3.png?raw=true)

The application Dockerfile is very simple, use node as a base image, copy the application files, download the application dependencies and run the application in the port 3000
![Welcome-Page](https://github.com/selaworkshops/npm-demo-app/blob/master/Images/Image4.png?raw=true)

## Build

Install Dependencies:
```
npm install
```

Run Tests:
```
npm test
```

create zip file
```
npm run build
```

Start the Application:
```
npm start
```

