---
sidebar_label: 'Event'
sidebar_position: 5
---

# Event Object
The Event object is a child of the WebRTC object and contains properties such as parent, socket, and events. The parent property points to the WebRTC object.

### `setup(parent)`
Configures the Event object.

#### Parameters
| Parameter | Type   | Description               |
|-----------|--------|---------------------------|
| parent    | WebRTC | Parent WebRTC object      |

### `listen()`
Sets up listeners for events received from the server via the socket.

#### Events List:
- `wait-accept-room-join`: Dispatches `onWaitUntilAdmit` after user acceptance
- `admit-user-to-join`: Dispatches `onRequestToAdmit` on join request
- `remove-user-from-waiting-list`: Dispatches `onCancelForAdmit` on removal
- `connect-room-success`: Dispatches `onConnectToRoomSuccess` on successful join
- `room-information`: Updates Room object's information property
- `user-connected`: Triggers `connectToNewUser` and `joinRoom` callback
- `user-left-room`: Executes People's `remove` and `leftRoom` callback
- `user-disconnected`: Same as `user-left-room` for disconnections
- `room-id-invalid`: Runs `invalidRoom` callback
- `run-action`: Executes server-requested custom actions
- `successfully-run-action`: Action success confirmation
- `failed-run-action`: Action failure notification
- `you-are-ban`: Triggers `banInRoom` callback
- `info-room-data`: Debug event for room information

### `addEventHandler(type, event, method)`
Adds a custom event handler.

#### Parameters
| Parameter | Type     | Description               |
|-----------|----------|---------------------------|
| type      | String   | Event category            |
| event     | String   | Specific event name       |
| method    | Function | Handler function          |

### `executeHandler(type, event, data)`
Executes the registered method for an event.

#### Parameters
| Parameter | Type   | Description               |
|-----------|--------|---------------------------|
| type      | String | Event category            |
| event     | String | Event name                |
| data      | Object | Event payload data        |



