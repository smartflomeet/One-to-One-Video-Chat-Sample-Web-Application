# 1-to-1 RTC: Web App using Node.js with Web Toolkit

1-to-1 RTC: A Sample Web App using Node.js with Web Toolkit
The Sample Web App demonstrates the use of APIs to develop basic 1-to-1 RTC (Real Time Communication) Application. The main motivation behind this application is to demonstrate usage of APIs and allow developers to ramp up on app by hosting on their own devices instead of directly using servers.

RTC Applications hosted run natively on supported set of web browsers without any additional plugin downloads.

This basic 1-to-1 Video Chat Application is developed using HTML, CSS, Bootstrap, JavaScript, jQuery, Node.js and EnxRtc (Web Toolkit).

## 1. Important!

When developing a Client Application with EnxRtc.js ( present in client/js ), make sure to replace the old EnxRtc.js with updated EnxRtc.js polyfills from https://doc.smartflomeet.ttns.in/developer/video-api/client-api/web-toolkit/ for RTCPeerConnection and getUserMedia. Otherwise your application will not work in web browsers.


## 2. Pre-Requisites

### 2.1 App Id and App Key

* Create your Project
* Get your App ID and App Key for that project

## 3. Installation
Two methods are provided 
- Setup everything using script or
- Follow step by step instructions to setup

### 3.1 Configure and run the app using Script
Prerequisite: latest version of `Node.js` and `git` Installed
* Downloads bash script file `script.sh` (https://github.com/smartflomeet/One-to-One-Video-Chat-Sample-Web-Application/blob/master/script.sh)
* Make it executable in linux terminal Using this command `sudo chmod +x script.sh`
* And just type `./script.sh` ( In same directory where your script.sh present)
* Give the information about configuration 
* That's it , You will see `localhost` listening to `port` you provided while setting up.

### 3.2 Step by Step process to configure and run the app (Jump to point 5. if you have followed 4.1)

#### 3.2.1 Clone project repository

* Clone this repository `git clone https://github.com/smartflomeet/One-to-One-Video-Chat-Sample-Web-Application.git --recursive`
### Please note `--recursive` option. Repo should be cloned recursively to download `client` app. 

#### 3.2.2 SSL Certificates or Self-Signed Certificates

The Application needs to run on https. So, you need to use a valid SSL Certificate for your Domain and point your application to use them.

However you may use self-signed Certificate to run this application locally. There are many Web Sites to get a Self-Signed Certificate generated for you, Google it. Few among them are:

* https://letsencrypt.org/
* https://www.sslchecker.com/csr/self_signed
* https://www.akadia.com/services/ssh_test_certificate.html

The following below can also be used to create a self-signed certificate.

For Mac/Linux

```javascript
  cd One-to-One-Video-Chat-Sample-Web-Application
  cd server
  mkdir certs
  sudo openssl req -x509 -newkey rsa:4096 -keyout ./certs/example.key -out ./certs/example.crt -days 10000 -nodes
  sudo chmod 755 ./certs/example.*
  cd ..
```
For Windows (Use Git Bash)

```javascript
  cd One-to-One-Video-Chat-Sample-Web-Application
  cd server
  mkdir certs
  openssl req -x509 -newkey rsa:4096 -keyout ./certs/example.key -out ./certs/example.crt -days 10000 -nodes
  chmod 755 ./certs/example.*
  cd ..
```
#### 3.2.3 Configure

Before you can run this application, configure the service. Copy the `server/example.env` as `server/.env` and update the values. Or you can set following system environment variables instead:

```javascript
  SERVICE_PORT - Node port on which your application will run. Default port set is 5000
  APP_ID - Your `App ID` - It's your username for API and can be found at Dashboard > Projects https://portal.smartflomeet.ttns.in/
  APP_KEY - Your `App Key` - - It's your password for API and can be found at Dashboard > Projects https://portal.smartflomeet.ttns.in/
```

For Mac and Linux, open a terminal window and type the following commands. Note - Replace all the characters after the `=` with values from your account:
```javascript
  export SERVICE_PORT=XXXX
  export APP_ID=XXXXXXXXXX
  export APP_KEY=XXXXXXXXX
```

On Windows, open a powershell / command window and type the following commands. Note that there is no `=`, just the key and value separated by a space:
```javascript
  setx SERVICE_PORT 'XXXX'
  setx APP_ID 'XXXXXXXXX'
  setx APP_KEY 'XXXXXXXXX'
```

### 3.2.4 Build

Run `npm install` to build the project and the build artifacts will be stored in the `./node_modules` directory.

### 3.2.5 Run Server

Run `node server.js` inside `server` folder to start your server.
```javascript
  cd server
  node server.js
```
Server started. Listening on Port 5000


## 4. Test Video Call

* Open a browser and go to `https://localhost:5000/`. The browser should load the App. Go to -> Advanced -> Proceed to localhost
* Don't have a Room ID? Create here (create a new RoomID)
* Store the Room ID for future use or share
* Enter a username (e.g. test0) as a moderator
* Join and allow access to camera and microphone when prompted to start your first webRTC call through 
* Open another browser tab and enter `https://localhost:5000/`
* Enter the same roomID previously created and add a different username (test1) as a participant and click join
* Now, you should see your own video in both the tabs!


## 5. Server API

 Server API is a Rest API service meant to be called from Partners' Application Server to provision video enabled
meeting rooms. API Access is given to each Application through the assigned App ID and App Key. So, the App ID and App Key
are to be used as Username and Password respectively to pass as HTTP Basic Authentication header to access Server API.

For this application, the following Server API calls are used:
* https://doc.smartflomeet.ttns.in/developer/video-api/server-api/rooms-route/#create-room - To create a room
* https://doc.smartflomeet.ttns.in/developer/video-api/server-api/rooms-route/#get-rooms - To get list of Rooms
* https://doc.smartflomeet.ttns.in/developer/video-api/server-api/rooms-route/#get-room-info - To get information of the given Room
* https://doc.smartflomeet.ttns.in/developer/video-api/server-api/rooms-route/#create-token - To create Token for the given Room


To know more about Server API, go to:
https://doc.smartflomeet.ttns.in/developer/video-api/server-api/


## 6. Client API

Client End Point Application uses Web Toolkit EnxRtc.js to communicate with Servers to initiate and manage RTC Communications.

To know more about Client API, go to:
https://doc.smartflomeet.ttns.in/developer/video-api/client-api/