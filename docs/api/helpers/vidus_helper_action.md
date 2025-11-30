---
sidebar_label: 'Action'
sidebar_position: 1
---

# Action Item
The Action item is a Vidus package helper for managing room actions.
To get action item, you can use core [getAction](../vidus-core/vidus_core_webrtc.md#getaction) method.

### `setAttributes()`
Set action attributes.

#### Parameters
| Parameter  | Type   | Description                |
|------------|--------|----------------------------|
| attributes | Object | Action attributes          |

### `setUsers()`
Run action for specific user in this room. If no user is selected, the action will run for all users.

#### Parameters
| Parameter | Type                                    | Description |
|-----------|-----------------------------------------|-------------|
| users     | String \| Array | A specific user's peer ID, or a list of selected users, where each user object in the list must include a peerJsId attribute.            |

### `setAsModeratorAction()`
Set the current action as a moderator-type action.

#### Parameters
| Parameter | Type    | Description                          |
|-----------|---------|--------------------------------------|
| status    | Boolean | Set action is moderator type action. |

### `request()`
Sends a request to the server to run the current action using the configured customization settings. This method calls the core room's [requestAction](../vidus-core/vidus_core_room.md#runRequestedActionAction) method.

### `run()`
Executes the action run method locally on the user's system. Implementation determines behavior: may show configuration UI or perform other operations.





