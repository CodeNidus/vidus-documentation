---
sidebar_label: 'Webrtc'
sidebar_position: 1
---

# WebRTC Class
This class handles the core logic for real-time video conferencing using WebRTC. It manages setup, connection, event handling, and utility functions for an integrated video communication experience.


---

## Core Methods

### `setup()`
Configures the WebRTC object for a video conference room. Initializes Room, Media, People, and Event objects as child components. Dispatches the `codenidus-vidus-setup` event after successful setup.

#### Parameters
This method accepts input as a single object with named properties.

| Parameter    | Type   | Description                        |
|--------------|--------|------------------------------------|
| options      | Object | 	Room configuration settings       |
| callback     | Object | Event handlers for room operations |
| connections  | Array  | Pre-existing user connections      |
| waitingList  | Array  | Users awaiting access to session   |
| userSettings | Object | User settings                      |

#### Example
```js
webrtc.setup({
      options: {
        name: 'joined-user-name',
        roomId: 'xxxxxxxxxxxx',
        localVideoRef: 'video-item',
        remoteVideoRef: 'remote-video',
        remoteAudioRef: 'remote-audio',
        resolution: 'hd'
      },
      callback: {
        joinRoom: userJoinRoom, // Called when a user joins the room
        leftRoom: userLeftRoom, // Called when a user leaves the room
        invalidRoom: invalidRoom, // Called if room ID is invalid
        exitConference: exitConference, // Called when a user exit from conference
        banInRoom: banInRoom, // Called when a user ban by moderator
      },
      connections: [],
      waitingList: [],
      userSettings: [],
    });
```

### `initial()`
Initializes the video conference with custom configurations.

#### Parameters

| Parameter | Type   | Description                    |
|-----------|--------|--------------------------------|
| configs   | Object | Custom configuration overrides |
| actions   | Object | Add custom actions             |
| themes    | Object | Add new custom theme           |
| overrides | Object | Method overrides               |

## Connection Management

### `connection()`
Manages socket connection state.

#### Parameters
| Parameter | Type    | Description                                   |
|-----------|---------|-----------------------------------------------|
| data      | Object  | Connection data                               |
| status    | Boolean | Connection state (true = open, false = close) |

### `initialPeerJs()`
Establishes connection with PeerJS server.

### `connectToNewUser()`
Handles new user connections.

#### Parameters
| Parameter | Type   | Description              |
|-----------|--------|--------------------------|
| data      | Object | New user connection data |


## Media Control

### `startStreamUserMedia()`
Initiates user media stream (video/audio/screen share) and establishes PeerJS connections.

### `getDevices()`
Retrieves available media devices (cameras, microphones, speakers).

## Event Management

### `on()`
Registers event listeners.

#### Parameters
| Parameter | Type     | Description         |
|-----------|----------|---------------------|
| type      | String   | Event category      |
| event     | String   | Specific event name |
| method    | Function | Handler function    |


### `callbackAction()`
Executes a callback action by name, as defined during the setup.

#### Parameters
| Parameter | Type   | Description                              |
|-----------|--------|------------------------------------------|
| name      | String | Defined callback method name             |
| data      | Any    | Any type data, passed to callback method |


## Utilities

### `runAction()`
Requests to run a specific action by name in the defined room. This method emits the `run-room-action` event to the server via the socket.

#### Parameters
| Parameter | Type   | Description                              |
|-----------|--------|------------------------------------------|
| roomId    | String | Target room id.                          |
| action    | Object | Action data by specific action structure |

### `camelToKebab()`
Converts camelCase to kebab-case.

#### Parameters
| Parameter | Type   | Description         |
|-----------|--------|---------------------|
| text      | String | Text for converting |


### `kebabToCamel()`
Converts kebab-case to camelCase.

#### Parameters
| Parameter | Type   | Description         |
|-----------|--------|---------------------|
| text      | String | Text for converting |


### `isMobileDevice()`
Detects mobile devices.

### `isFirefox()`
Detects Firefox browser.


### `notify()`
Displays system notification.

#### Parameters
| Parameter | Type   | Description          |
|-----------|--------|----------------------|
| title     | String | Notification title   |
| text      | String | Notification message |

### `getUserToken()`
Retrieves or generates user authentication token.

#### Parameters
| Parameter | Type     | Description                       |
|-----------|----------|-----------------------------------|
| next      | Function | Success callback (receives token) |
| error     | Function | Error callback                    |

### `createRoom()`
Creates new conference room.

#### Parameters
| Parameter | Type   | Description        |
|-----------|--------|--------------------|
| data      | Object | Room configuration |

### `getRoomsList()`
Retrieves available rooms list.




