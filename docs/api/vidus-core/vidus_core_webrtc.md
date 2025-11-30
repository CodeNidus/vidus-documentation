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

##### Options attributes
---
**name** `string`
room joining user name

**roomId** `string`
joning room id

**localVideoRef** `string`
Theme local user video element id

**remoteVideoRef** `string`
Theme joined user video element id

**remoteAudioRef** `string`
Theme joined user audio element id

**resolution** `string`
Joined user stream video resolution 


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

### `openConnection()`
Open socket connection.

#### Parameters
| Parameter | Type    | Description                                   |
|-----------|---------|-----------------------------------------------|
| token     | String  | User authorization token                      |

### `closeConnection()`
Close socket connection.

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

## Event Management

### `on()`
Registers event listeners.

#### Parameters
| Parameter | Type     | Description         |
|-----------|----------|---------------------|
| type      | String   | Event category      |
| event     | String   | Specific event name |
| method    | Function | Handler function    |

### `emit()`
Trigger a CustomEvent event.

#### Parameters
| Parameter | Type   | Description     |
|-----------|--------|-----------------|
| type      | String | Event name      |
| data      | Object | Additional data |


## Utilities

### `getAction()`
Retrieves a specific action item by its unique name. The returned action item can perform one of two functions:
1.  **Execute the Action:** Run the current action in a predefined room.
2.  **Configure the Action:** Open the management section (UI) to set up the action's properties.

#### Parameters
| Parameter   | Type    | Description                              |
|-------------|---------|------------------------------------------|
| name        | String  | Target room id.                          |
| attributes  | Object  | Action data by specific action structure |
| users       | Array   | Action execute users list                |
| moderator   | Boolean | Action moderator type                    |


### `registerActionReference()`
Register action reference item.

#### Parameters
| Parameter | Type    | Description               |
|-----------|---------|---------------------------|
| name      | String  | Action name               |
| object    | Object  | Action reference          |


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

### `can()`
Check user has a specific ability or not.

#### Parameters
| Parameter | Type   | Description  |
|-----------|--------|--------------|
| name      | String | Ability name |


### `createRoom()`
Creates new conference room.

#### Parameters
| Parameter | Type   | Description        |
|-----------|--------|--------------------|
| data      | Object | Room configuration |

### `getRoomsList()`
Retrieves available rooms list.

### `getDevTools()`
Returns development utility methods for use within actions. Provides access to WebRTC core functionality and common operations.

#### Methods
| Method               | Description                                                            |
|----------------------|------------------------------------------------------------------------|
| `core()`             | WebRTC core instance                                                   |
| `getConfigs()`       | Retrieves WebRTC configuration settings                                |
| `getPeerJsId()`      | Returns current connection's peer ID                                   |
| `getSocket()`        | Returns WebRTC socket instance                                         |
| `getConnections()`   | Gets connections for all users currently in the room                   |
| `emit()`             | Triggers a custom event                                                |
| `notify()`           | Displays a notification message                                        |
| `leftRoom()`         | Leaves the current room                                                |
| `muteCamera()`       | Disables the user's camera                                             |
| `muteMicrophone()`   | Disables the user's microphone                                         |
| `unmuteCamera()`     | Enables the user's camera                                              |
| `unmuteMicrophone()` | Enables the user's microphone                                          |
| `getRequest()`       | Gets authorized request (with `true`) or simple request (with `false`) |
| `getToken()`         | Retrieves user authorization token                                     |

