# MeanPeriod6
### Question 1: Explain the concept of Hybrid Mobile App Development?

Hybrid apps are like websites developed using the same tchnologies, HTML, CSS, JavaScript. But can be delpoyed on phones and tablets like native apps, because they are "basically" a website running in a native app container on the device, using the device WebView. 

![](http://developer.telerik.com/wp-content/uploads/2015/03/hybrid-app-architecture.png)

### Question 2: Explain the Pros & Cons of using Hybrid Mobile App Development compared to Native App Development?

##### Pro's 
* Multi platform, you don't need to be profficient in multiple languages to create and app for both Android and iOS
* Deployed in app store, compared to a HTML5 app
* Unlimited possibilities because its created with HTML

##### Con's
* Loading might be slow compared to Native apps
* They don't feel as great as native apps


### Question 3: Explain about the "building blocks" involved in an ionic Hybrid Application?

![](http://image.slidesharecdn.com/aqdcjl9zqhcxm1noviyy-signature-7873c75031ac31677418d06ca1135ba58cf1db5a062456d83a04778887726afe-poli-151012220109-lva1-app6891/95/build-consumer-apps-using-mobile-sdk-and-ionic-framework-10-638.jpg?cb=1444691183)

Ionic uses Cordova to get access to the native mobile fatures, like the camera and geolocation. Gulp.JS is used for automation of application development. It also uses AngularJS as the "Foundation" of the app, and the HTML is then styled using CSS, like BootStrap does.


### Question 4: Explain and demonstrate ways to debug Hybrid Mobile Applications Running on a real device?
1. Enable USB debugging on your device: https://developer.chrome.com/devtools/docs/remote-debugging
2. Open Chrome on your desktop (development) machine and navigate to: chrome://inspect
3. Select Discover USB Devices.
4. Select your device.
5. To use your device to debug a web application that’s running on your development machine: 



Click Port forwarding….
Set the device port and the localhost port.
Select Enable port forwarding. See https://developer.chrome.com/devtools/docs/remote-debugging#port-forwarding for details.


1. First ordered list item
2. Another item
⋅⋅* Unordered sub-list. 
1. Actual numbers don't matter, just that it's a number
⋅⋅1. Ordered sub-list
4. And another item.

### Question 5: Explain what the WebSocket Protocol brings to the Web-world?
It brings TCP sockets that we know from Java to the world of web-development, making actual realtime transactions possible. And not using some phony method like long-polling or http streaming.


### Question 6: Explain and demonstrate the process of WebSocket communication - From connecting client to server, through sending messages, to closing connection?
When a connection through a websocket is opened it all start with a "Handshake" the same principle as when using token authentication. After the handshake the connection is now open, and the client can sends messages to the server and the other way around, as many times as needed. When the transactions is over, either the client or the server closes the connection.

![](https://www.pubnub.com/static/images/get-started/websockets_guides.png)


### Question 7: What's the advantage of using libraries like Socket.IO, Sock.JS, WS, over pure WebSocket libraries in the backend and standard APIs on frontend? Which problems do they solve?
* Easier to use, maintained
* Crossbrowser compatability is already developed for it
* Fallbacks to other technologies if client browser is not compatible


### Question 8: What is Backend as a Service, Database as a Service, why would you consider using Firebase in your projects?
Backend as a Service (BaaS), is cloud based infrastructure for mobile and web apps. Its simply cloud computing for developers to make easy scalable applications for mobile and web.  

DataBase as a Service (DBaaS) is a cloud based database approach, to create scalable and felxible data storage in the cloud. 

FireBase is not any ordinary DBaaS, it's a real-time scalable backend that provides the tools to quickly build applications for millions of users. 


### Question 9: Explain the pros & cons of using a Backend as a Service Provider like Firebase?
#### pro's 
* Scalable
* Flexible
* Easy to use
* Possibility for Authentication
* Possibility for hosting
#### con's
* Lack of control over network performance issues, such as unacceptable latency 
* "Pay per view", pay for the bandwidth you use

### Question 10: Explain and demonstrate "three-way data binding" using Firebase and Angular?
When using AngularJS the scope of our controller and view stay synced creating a 2-way databinding (ng-model). Using firebase as a backend makes it possible to create 3-way databinding. We can bind the datamodel of our AngularJS app and a FireBase location like "https://xxx.firebaseio.com/users", this way whenever the model on FireBase changes the updates are automatically pushed to the front-end and the other way round.

Refer to [Thinkster tutorial]

### Question 11: Explain and demonstrate the difference between the simple chat system in your own WebSocket + Node.js backend vs. Firebase?
In AngularJS you have to create a connection to the client, and everytime a message is sent you need to add that to a local scope variable and call ``` $scope.$apply ``` to make sure AngularJS updates the scope.  
See [SimpleChat]

Where as in Firebase you only need a few lines of code, and that small app is even scalable from the beginning. 
```javascript
var ref = new Firebase("https://xxx.firebaseio.com/");
var messagesRef = ref.child('messages');

scope.messages = $firebaseArray(messagesRef);

scope.sendMessage = function() {
  scope.messages.$add({
    body: scope.messageInput
  });
  scope.messageInput = '';
};
```

[Thinkster tutorial]: <https://github.com/JonasRafn>
[SimpleChat]:<https://github.com/JonasRafn/SimpleChatSocket>