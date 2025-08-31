---
sidebar_label: 'Media'
sidebar_position: 3
---


# Media Object
The Media object is a child of the WebRTC object manage user media actions during video conference.

### `setup()`
Configures the Media object, including setting up the user video renderer canvas, video resolution, and screen sharing.

#### Parameters
| Parameter | Type   | Description               |
|-----------|--------|---------------------------|
| parent    | WebRTC | Parent WebRTC object      |
| options   | Object | Media configuration       |

#### Usage
```js
setup(parent, {
  resolution: 'hd',
  remoteVideoRef: 'remote-vide-ref',
  localVideoRef: 'local-video-ref',
  remoteAudioRef: 'remote-audio-ref',
})
```

### `grab()`
Captures the user's video and audio media using the specified device IDs.

#### Parameters
| Parameter | Type    | Description               |
|-----------|---------|---------------------------|
| devices   | Object  | Devices IDs configuration |
| muteVideo | Boolean | Camera mute status        |
| muteAudio | Boolean | Microphone mute status    |

#### Usage
```js
grab(devices, muteVideo = false, muteAudio = false)
```

### `setInterval()`
Calibrates the user stream's FPS based on the WebRTC object's configuration.

### `processOnMedia()`
Renders the user's media on the canvas and applies processing.

### `blurBackground()`
Toggles the blur effect on the user's video background by body segment module.

### `registerFaceDetectorCallback()`
Registers methods to be executed after face detection.

#### Parameters
| Parameter | Type     | Description               |
|-----------|----------|---------------------------|
| name      | String   | Callback name             |
| callback  | Function | Callback function         |

#### Usage
```js
registerFaceDetectorCallback('callback name', () => {
  console.log('Face Detector callback');
})
```

### `release()`
Releases the user's captured media.

### `resetConnectionsStream()`
Resets the connection stream with all connected users.

### `streamVideo()`
Streams video to a DOM video element.

#### Parameters
| Parameter | Type   | Description               |
|-----------|--------|---------------------------|
| peerJsId  | String | Target peer ID            |
| media     | Object | Media stream              |
| options   | Object | Streaming options         |

#### Usage
```js
streamVideo('unique-peer-id', media, {
  customReference: 'custom-optional-ref',
  videoMute: false,
  eventListener: false
})
```

### `streamAudio()`
Streams audio to a DOM audio element.

#### Parameters
| Parameter | Type   | Description               |
|-----------|--------|---------------------------|
| peerJsId  | String | Target peer ID            |
| media     | Object | Media stream              |

#### Usage
```js
streamAudio('unique-peer-id', media)
```

### `setEvent()`
Registers an event handler.

### `muteCamera()`
Turns off the user's camera.

### `muteMicrophone()`
Turns off the user's microphone.

### `resetConnectionsVideoAudioMedia()`
Resets the user's media connections with other joined users.

#### Parameters
| Parameter | Type   | Description               |
|-----------|--------|---------------------------|
| media     | Object | New media source          |

#### Usage
```js
resetConnectionsVideoAudioMedia(media)
```

### `sendUserMediaMuteStatusByDataConnection()`
Sends mute status to other joined users.

#### Parameters
| Parameter    | Type    | Description               |
|--------------|---------|---------------------------|
| videoStatus  | Boolean | Camera mute status        |
| audioStatus  | Boolean | Microphone mute status    |

#### Usage
```js
sendUserMediaMuteStatusByDataConnection(false, false)
```

### `terminateConnectionsVideoAudioMedia()`
Terminates the current stream with other joined users.

#### Parameters
| Parameter | Type   | Description               |
|-----------|--------|---------------------------|
| type      | String | 'video' or 'audio'        |

#### Usage
```js
terminateConnectionsVideoAudioMedia('video')
```

### `setConnectionMediaStatus()`
Sets the user's camera and microphone status.

#### Parameters
| Parameter | Type   | Description               |
|-----------|--------|---------------------------|
| data      | Object | Status data               |

#### Usage
```js
setConnectionMediaStatus({
  peerJsId: 'unique-peer-id',
  camMute: false,
  micMute: false
})
```

## BodySegment Object
The BodySegment object is a child of the Media object.

### `blur()`
Applies a blur effect to the video background.

#### Parameters
| Parameter     | Type    | Description               |
|---------------|---------|---------------------------|
| bodySegmenter | Object  | Body segmenter instance   |
| canvas        | Object  | Canvas element            |

#### Usage
```js
blur(bodySegmenter, canvas)
```

---

## FaceDetect Object
The FaceDetect object is a child of the Media object.

### `detect()`
Detects the user's face in the video stream.

#### Parameters
| Parameter    | Type    | Description               |
|--------------|---------|---------------------------|
| faceDetector | Object  | Face detector instance    |
| canvas       | Object  | Canvas element            |


#### Usage
```js
detect(faceDetector, canvas)
```

---

## ScreenShare Object
The ScreenShare object is a child of the Media object.

### `startShareScreen()`
Starts streaming the user's screen.

### `stopShareScreen()`
Stops streaming the user's screen.

### `callToNewJoinedUser()`
Streams the user's screen to a newly joined user.

### `eventTrigger()`
Dispatches screen share status event. `onScreenShareModule`

#### Parameters
| Parameter | Type    | Description               |
|-----------|---------|---------------------------|
| status    | Boolean | Screen share status       |

#### Usage
```js
eventTrigger(true)
```

### `closeScreenShare()`
Closes the screen share video area.

#### Usage
```js
closeScreenShare({
  peerJsId: 'screen-shared-user-unique-peer-id',
})
```

#### Parameters
| Parameter | Type   | Description               |
|-----------|--------|---------------------------|
| data      | Object | Close event data          |

---

## ScreenRecord Object
The ScreenRecord object is a child of the Media object.

### `listenToEvents()`
Listens to media stream reset events.

### `startRecord()`
Starts screen recording.

### `stopRecord()`
Stops screen recording.

### `mixMicScreenAudioStreams()`
Mixes microphone and screen audio.

### `processRecordedVideo()`
Processes recorded media with FFmpeg.

### `saveData()`
Saves recorded media.

### `cleanup()`
Cleans up recording variables.

### `isRecordingScreen()`
Checks if screen is recording.

### `eventTrigger()`
Dispatches screen record status event. `onScreenRecordModule`



