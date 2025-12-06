---
sidebar_label: 'Creating custom actions'
sidebar_position: 2
---

# Custom action structure
Custom actions follow a standardized structure defined by the framework.
Each action must be placed inside its own folder, and this folder must contain the following files:
- index.js — the action entry point that defines metadata and imports other parts
- customAction.js — the action handler (execution logic running on the client)
- customAction.vue — the client-side UI component responsible for triggering the action and sending the request to the server

This structure ensures a clean separation between metadata, UI, and execution logic.

## Step 1: Create `index.js`
The index.js file acts as the metadata and importer file for your custom action.
It ties the action script and Vue component together so they can be registered and used by the system.

#### Example
```js
import script from './customAction.js';
import view from './customAction.vue';

export default {
  name: 'custom-action',
  script: script,
  view: view
};
```

#### Fields
- **name** — unique identifier for the action
- **script** — the JavaScript file that contains the execution logic
- **view** — Vue component that provides the UI for triggering the action

*Both script & view triggering by a run method.*

## Step 2: Create `customAction.vue`
The Vue component acts as the client-side interface for your custom action.
Its purpose is to provide the UI, collect input from the user (if needed), and send the action request to the server.

It usually contains:
- a UI element (button, menu item, dialog, etc.)
- a run method that triggers the action request
- optional user interaction logic (forms, confirmations, parameters, etc.)

#### Required: The `run` Method
Every custom action Vue component must define a run method and expose it using defineExpose().
This makes the method accessible from outside the component so the framework can call it when needed.


#### Props
The component receives several useful props, automatically injected by the framework:
- **room** — the current room object
- **webrtc** — the WebRTC core instance
- **userSettings** — user preferences and metadata

#### Example
```html
<script setup>

  // Access component props
  const props = defineProps({
    room: Object,
    webrtc: Object,
    userSettings: Object,
  });

  // Required `run` method
  const run = (room, data) => {
    // Check the user’s permissions (example: only the creator can run this action)
    if (!props.userSettings.isCreator) return;

    // Use local helper functions
    logText('custom text');

    // Get the action instance
    const action = props.webrtc.getAction('custom-action');

    // Configure the action
    action.setAsModeratorAction();
    action.setAttributes({
      customParameters: {...data }
    });
    action.setUsers([
      { peerJsId: "user-1-peerJsId" },
      { peerJsId: "user-2-peerJsId" }
    ]);

    // Send the request to the server
    action.request();
  }

  // Example helper function
  const logText = (text) => {
    console.log(text);
  }

  // Expose the run method so it can be called externally
  defineExpose({
    run,
  });
</script>

<template>
  <button @click="run">Run Custom Action</button>
</template>
```

In your Vue action component, you can use the **VCDialog** framework component to display popup dialog boxes for confirmations, additional user input, or advanced UI interactions.


## Step 3: Create `customAction.js`
The customAction.js file contains the execution logic that runs on the client machine after the server approves the action request.
This script is the core of your action’s functionality and is responsible for performing the actual behavior—such as modifying the UI, interacting with the canvas, updating the room state, or running any custom JavaScript code.

Unlike the Vue component, this file:
- does not contain UI logic
- does not run inside Vue’s reactivity system
- executes only when the server instructs the client to run the action

This ensures a clean separation between UI (Vue) and action logic (JS).

#### Required: The `run` Method
A valid action script must export an object containing a run method:


#### Parameters
The run method receives two parameters:

**context** — Provides [development utility methods](../../api/vidus-core/vidus_core_room.md#getdevtools)
**payload** — Action data, sent from the Vue component during the action request. This allows you to pass custom parameters such as form values, user selections, or configuration options.

#### Example
```js
module.exports = () => {
  const action = {
    counter: 0,
  };
  
  
  action.run = (context, payload) => {
    console.log("Custom action executed:", payload);

    action.counter++;
    
    // Check action parameters
    if (payload?.showNotification) {
      context.notify("Action triggered successfully!");
    }

    alert("Action call time:", action.counter);
  };
  
  return action;
};
```




