---
sidebar_label: 'Room'
sidebar_position: 2
---

# Room Object
The Room object is a child of the WebRTC object and manage room necessary actions.

### `setup(parent, options)`
Configures the Room object.

#### Parameters
| Parameter | Type   | Description                |
|-----------|--------|----------------------------|
| parent    | WebRTC | Parent WebRTC object       |
| options   | Object | Room configuration options |

### `join(roomId, userData)`
Requests to join a specific room by emitting the `join-room` event to the server.

#### Parameters
| Parameter | Type   | Description                     |
|-----------|--------|---------------------------------|
| roomId    | String | Target room ID to join          |
| userData  | Object | User information for joining    |

### `notifyJoinSuccess(roomId)`
Notifies the server that the join process was successful and the user has joined the room.

#### Parameters
| Parameter | Type   | Description                     |
|-----------|--------|---------------------------------|
| roomId    | String | Room ID where join succeeded    |

### `left(roomId, userData)`
Handles the user leaving the room. It closes all connections with other users, releases the user's media, and stops screen sharing if it is active. This method emits the `left-room` event to the server.

#### Parameters
| Parameter | Type   | Description                     |
|-----------|--------|---------------------------------|
| roomId    | String | Room ID being left              |
| userData  | Object | User information for departure  |

### `runRequestedAction(action)`
Executes an action requested by other users. It dispatches a custom event of the form `on{ActionName}Action`.

#### Parameters
| Parameter | Type   | Description                     |
|-----------|--------|---------------------------------|
| action    | Object | Action object to execute        |





