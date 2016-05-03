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
5. To use your device to debug a web application that’s running on your development machine
6. Click Port forwarding….
7. Set the device port and the localhost port.
8. Select Enable port forwarding. See https://developer.chrome.com/devtools/docs/remote-debugging#port-forwarding for details.


### Question 5: Explain when and why CORS is a problem for Hybrid Mobile Applications?
Cross Origin Ressource Sharing (CORS) is a safety feature in modern browsers that does not allow the website make an HTTP request to a url that is not the same as the root of the site. This can cause problems in Hybrid App development when trying to use an API like Google Maps that has a different url than the app has when developing it. 

### Question 6: Explain how and why it is possible for a Hybrid Application to access native phone devices like location, calendar etc?
Hybrid Apps use frameworks like Cordova or PhoneGap, access the native features of the phone. These frameworks has API's that can access these features,this makes development easy for us. 

![](http://image.slidesharecdn.com/0809cordova-140407070826-phpapp01/95/apache-cordova-4-638.jpg?cb=1396854760)


### Question 7: Explain using an example the "fundamentals" of an ionic application?
Ionic uses AngularJS and Cordova to create Hybrid Apps, for the styling of this app Ionic uses CSS and JavaScript like BootStrap does. 
When creating the HTML for a the app, Ionic specific directives is used like this.
```html
<ion-view view-title="Favorites | {{ username }}" class="favorites-page">
    <ion-nav-buttons side="right">
        <button class="button" ng-click="logout()">
            Log out
        </button>
    </ion-nav-buttons>
    <ion-content>

        <ion-list>
            <ion-item ng-repeat="song in favorites" class="item-avatar" ng-click="openSong(song)">
                <img ng-src="{{ song.image_small }}">
                <h2>{{ song.title }}</h2>
                <p>{{ song.artist }}</p>

                <ion-option-button class="button-assertive" ng-click="removeSong(song, $index)">
                    <i class="ion-minus-circled"></i>
                </ion-option-button>
            </ion-item>
        </ion-list>


    </ion-content>
</ion-view>
```


### Question 8: Explain using an example how your Hybrid Application communicates with a backend and how CORS problems were solved (if any)?

My app uses jQuery to make requestz to an external api.
```javascript
o.getNextSongs = function () {
            return $http({
                method: 'GET',
                url: SERVER.url + '/recommendations'
            }).success(function (data) {
                o.queue = o.queue.concat(data);
            });
        };
```
To solve CORS problems you need to setup a proxy server that sends our request to the the real api.  
To do this setup ```ionic.project``` like this.
```json
{
  "name": "proxy-example",
  "app_id": "",
  "proxies": [
    {
      "path": "/api",
      "proxyUrl": "http://cors.api.com/api"
    }
  ]
}
```

For more examples see [IonicSongApp]

[IonicSongApp]: <https://github.com/JonasRafn/ionicsongapp>