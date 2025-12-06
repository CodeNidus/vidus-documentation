---
sidebar_label: 'Adding custom actions'
sidebar_position: 3
---

# Adding custom actions to a project
To integrate a custom action with your project, follow these steps:

### 1. Place the Action Files
Locate your custom action folder (containing index.js, customAction.js, and customAction.vue) within your project structure. A recommended location is the utils directory or a dedicated actions folder.

### 2. Import the Custom Action
Import the action into the file where you initialize your VidusCreator instance:

```js
import customAction from "./utils/customAction";
```
### 3. Configure VidusCreator Options
Add the imported action to the actions object within your VidusCreator configuration:

```js
const videoconference = VidusCreator({
    actions: {
        customAction: customAction
    }
});
```



