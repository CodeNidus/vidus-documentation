---
sidebar_label: 'People'
sidebar_position: 4
---


# People Object
The People object is a child of the WebRTC object and contains properties such as parent, connections, waitingList, and options. The parent property points to the WebRTC object.

### `setup(parent, connections, waitingList, options)`
Configures the People object.

#### Parameters
| Parameter    | Type   | Description                     |
|--------------|--------|---------------------------------|
| parent       | WebRTC | Parent WebRTC object            |
| connections  | Array  | Initial connected users list    |
| waitingList  | Array  | Initial waiting users list      |
| options      | Object | People configuration options   |

### `add(mediaConnection, dataConnection, data)`
Adds a new connected user to the connections list.

#### Parameters
| Parameter       | Type   | Description                     |
|-----------------|--------|---------------------------------|
| mediaConnection | Object | User's media connection        |
| dataConnection  | Object | User's data connection         |
| data            | Object | User information               |

### `remove(data)`
Removes a user who has left the room from the connections list.

#### Parameters
| Parameter | Type   | Description                     |
|-----------|--------|---------------------------------|
| data      | Object | User data to remove             |

### `closeAll()`
Closes all media and data connections with users in the connections list.

### `getConnections()`
Retrieves the list of connected users.

### `addToWaitingList(data)`
Adds a user who has requested to join the room to the waiting list.

#### Parameters
| Parameter | Type   | Description                     |
|-----------|--------|---------------------------------|
| data      | Object | User data to add                |

### `removeFromWaitingList(index)`
Removes a user from the waiting list by index.

#### Parameters
| Parameter | Type   | Description                     |
|-----------|--------|---------------------------------|
| index     | Number | Waiting list index to remove    |

### `removeFromWaitingListByPeerJsId()`
Removes a user from the waiting list by PeerJS ID.

### `setData(peerJsId, key, value, options)`
Sets custom data (key/value) for a user in the connections list.

#### Parameters
| Parameter | Type   | Description                     |
|-----------|--------|---------------------------------|
| peerJsId  | String | Target user's PeerJS ID         |
| key       | String | Data key to set                 |
| value     | Any    | Data value to set               |
| options   | Object | Additional options              |

### `findOne(key, value)`
Finds the first user in the connections list based on a specific key and value.

#### Parameters
| Parameter | Type   | Description                     |
|-----------|--------|---------------------------------|
| key       | String | Property key to search          |
| value     | Any    | Value to match                  |

### `find(key, value)`
Finds all users in the connections list based on a specific key and value.

#### Parameters
| Parameter | Type   | Description                     |
|-----------|--------|---------------------------------|
| key       | String | Property key to search          |
| value     | Any    | Value to match                  |




