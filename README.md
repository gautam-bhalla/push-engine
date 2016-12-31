
> This is a self contained push notification module for iOS devices using Apple Push Notification (APN) and for Android using Google Cloud Messaging (GCM).


## Install

npm release is still in progress.


## Usage


//Import the Module.
var PushNotification = require('./push-notification');
var DeviceType = PushNotification.DeviceType;
var path = require('path');

//Configure the credentials.
PushNotification.init({
	apn: {
		cert: path.resolve('./keys/cert.pem'),
		key: path.resolve('./keys/key.pem')
	},
	gcm: {
		apiKey: 'gcm-api-key'
	}
});

//Configure Parameters.
var iosToken = 'apple-device-token';
var androidToken = 'android-device-token';
var message = 'Push Message....';
var badge = null;
var sound = null;
var payload = null;

// Sending push to a single device.
PushNotification.pushSingle(DeviceType.IOS, iosToken, message, badge, sound, payload);
PushNotification.pushSingle(DeaviceType.ANDROID, androidToken, message, badge, sound, payload);

// Sending push to multiple devices.
PushNotification.prepare(message, badge, sound, payload);
PushNotification.addTarget(DeviceType.IOS, iosToken);
PushNotification.addTarget(DeviceType.ANDROID, androidToken);
PushNotification.addTarget(DeviceType.ANDROID, anotherToken);
PushNotification.push();
```


## Configuration

### Apple Platform-  Apple Push Notification (APN).
- Please refer to this link- <https://github.com/argon/node-apn/wiki/Preparing-Certificates>

### Android Platform - Google Cloud Messaging (GCM).
- Please refer to this link<https://developers.google.com/cloud-messaging/gcm#senderid>
