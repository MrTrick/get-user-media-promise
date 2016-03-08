# get-user-media-promise

[![Build Status](https://travis-ci.org/nfriedly/get-user-media-promise.svg?branch=master)](https://travis-ci.org/nfriedly/get-user-media-promise)
[![npm-version](https://img.shields.io/npm/v/get-user-media-promise.svg)](https://www.npmjs.com/package/get-user-media-promise)
![bower-version](http://badge.fury.io/bo/get-user-media-promise.svg)

Light-weight wrapper for the newer [Promise]-based [MediaDevices.getUserMedia] API with a fallback to the deprecated [navigator.getUserMedia] (and it's prefixed variants).

Less than 0.5kb after minification and gzipping (about 5% of the size of the [other] getUserMedia shim).

**Note**: this will only work in web browsers, and only [fairly current ones](http://caniuse.com/#feat=stream) at that. 

Additionally, this library does not attempt to reformat constraints for cross-browser support, so if you need advanced audio/video constraints, the [other library][other] may be a better choice.

## Installation:

### npm

    npm install --save get-user-media-promise
    
### Bower

    bower install --save get-user-media-promise
    
### Standalone
 
 Download the [latest release](https://github.com/nfriedly/get-user-media-promise/releases) from GitHub.

## Usage: 

 * With a bundler such as Require.js, Browserify, or WebPack: require() the module and it returns a `getUserMedia()` method that will always return a Promise or Promise-like object.
 * As a standalone library: when neither `define()` nor `module` are defined, the module will go into pollyfill mode, setting `navigator.mediaDevices.getUserMedia()` if that method is not already defined and doing nothing if it is.
 
 Then:
 
```js
var getUserMedia = require('get-user-media-promise'); // or navigator.mediaDevices.getUserMedia when used standalone

getUserMedia({audio: true, video: true})
  .then(function(mediaStream) {
    console.log(mediaStream);
  })
  .catch(function(error) {
    console.log('error');
  });
```

[MediaDevices.getUserMedia]: https://developer.mozilla.org/en-US/docs/Web/API/MediaDevices/getUserMedia
[Promise]: https://developer.mozilla.org/en-US/docs/Web/API/Promise
[navigator.getUserMedia]: https://developer.mozilla.org/en-US/docs/Web/API/Navigator/getUserMedia
[other]: https://www.npmjs.com/package/getusermedia
