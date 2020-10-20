# EC601-Project03
Author Name: Lin Cheng (U14828854)
Due Date: 10/19/2020
Project Name: EC601-Project03

## 1.Description

This is a repository for EC601 Project03. This project is to test the WebRTC JavaScript code samples and analyze the signaling and find security holes in session creation. All of the codes of these samples can be found at https://github.com/chengl11/samples.


## 2.Testing Step

1. Fork the copy of https://github.com/webrtc/samples into my account https://github.com/chengl11/samples.

2. Open repository in VS Code by using GitHub Desktop.
![Image of github-destop](https://github.com/chengl11/EC601-Project03/blob/main/images/github-destop.png)
![Image of samples-code-in-VSCode](https://github.com/chengl11/EC601-Project03/blob/main/images/samples-in-vscode.png)

3. Open index.html in my browser Chrome.
![Image of main-page-of-samples in](https://github.com/chengl11/EC601-Project03/blob/main/images/samples-in-vscode.png)

4. Open samples and test each of them.

### 4.1 Testing getUserMedia
![Image of Basic-getUserMedia-demo](https://github.com/chengl11/EC601-Project03/blob/main/images/Basic-getUserMedia-demo.png)

This example consists of four parts.

#### 4.1.1 init function
![Image of getusermedia-init](https://github.com/chengl11/EC601-Project03/blob/main/images/getusermedia-init.png)

This function calls the WebRTC "navigator.mediaDevices.getUserMedia(constraints)" API. When the call succeeds, it goes to the “handleSuccess” function section. When the call fails, it goes to the “handleError” function section

#### 4.1.2 handleSuccess function
![Image of getusermedia-handlesuccess](https://github.com/chengl11/EC601-Project03/blob/main/images/getusermedia-handlesuccess.png)

This function attempts to get the permission of user's camera. When the user clicks the "Open Camera" button on the page, a prompt at the top left corner of the browser appears and shows that "This File wants to use your camera. Allow or Block?" When the user allows the website to use the camera, Chrome's Console displays "Got Stream with constrains: {audio:false, video:true}" and "Using video device: XXX" to indicate successful camera call. If the user refuses to call the camera, it goes to the "handleError" function.

#### 4.1.3 handleError function
![Image of getusermedia-handleerror](https://github.com/chengl11/EC601-Project03/blob/main/images/getusermedia-handleerror.png)

This function will handle two errors. The first is called 'ConstraintNotSatisfiedError', when produce this kind of error, this part will be a period of "The resolution ${v.w idth. The exact} x ${v.h eight. The exact} px is not supported by your device." The error message is sent to The third "errorMsg" function. Another error is when the user refuses to use the camera, and this error also known as 'PermissionDeniedError'. This section will sent the message “Permissions have not been granted to use your camera and ' + 'microphone, you need to allow the page access to your devices in ' + 'order for the demo to work” to the third "errorMsg"function. Finally, it receives other errors and sends it to the third "errorMsg"function as well.

#### 4.1.3 errorMsg function
![Image of getusermedia-errormsg](https://github.com/chengl11/EC601-Project03/blob/main/images/getusermedia-errormsg.png)

This function takes the error message given by the "handleError" function and displays it on the page for the user to see.

### 4.2 other Tests

#### 4.2.1 Testing RTCDataChannel(transmit text)
![Image of transmit-text.png](https://github.com/chengl11/EC601-Project03/blob/main/images/transmit-text.png)

This sample shows how to transmit text on the web page. It works by clicking the "Start" button and then entering the desired message in the "Send" box below. When you have finished typing, click the “Send” button, and the other Receive box displays what you just sent. And then click the “Stop” button to end the Transmit.

#### 4.2.2 Testing RTCPeerConnection
![Image of basic-peer-connection-demo](https://github.com/chengl11/EC601-Project03/blob/main/images/basic-peer-connection-demo.png)

This sample shows how to setup a connection between two peers using RTCPeerConnection. 


### 5. Analysis of signaling and security

Because WebRTC does not specify a signaling protocol, the encryption mechanism obviously depends on the signaling protocol of choice. One of the major protocols is SIP. The Session Initiation Protocol (SIP) is a Protocol proposed as a standard for the creation, modification, and termination of interactive user sessions involving video, voice, instant messaging, online gaming, and virtual reality.

But SIP protocol also has many security holes. SIP is a widely implemented standard for establishing and disconnecting telephony in VoIP communications. However, it is a text-based protocol, incorporating many elements of the Hypertext Transfer Protocol (HTTP) and the Simple Mail Transfer Protocol (SMTP). Because it uses plain text messages to exchange information, any malicious party can take advantage of the network to capture SIP messages. If an attacker can read a user's sensitive information, they can use this information to trick the user.

For instance, in 4.2.1, that sample implements the sending and receiving of text messages. If this example uses SIP as a signaling protocol, then there is a potential risk. A hacker or other malicious person may capture SIP information to collect information sent by the user.


### 6. Reference

Security in a SIP network: Identifying network attacks.
searchunifiedcommunications.techtarget.com. Accessed on 2015-07-28.

A Study of WebRTC Security. (n.d.). Retrieved October 20, 2020, from https://webrtc-security.github.io/
