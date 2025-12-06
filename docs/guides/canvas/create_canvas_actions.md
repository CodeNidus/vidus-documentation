---
sidebar_label: 'Creating Canvas Actions'
sidebar_position: 2
---
# Creating Canvas Actions
To create a custom canvas action, follow the standard custom action structure with these additional requirements:

- Set category: `canvas` in your action's metadata
- Specify an `icon` using the Material Design Icons (MDI) library & set to action's metadata too.
- Implement canvas-specific logic in your action handler

Canvas actions appear as toolbar buttons when the canvas is active, allowing participants to trigger drawing and annotation tools.

#### Example: Canvas Action Metadata

```js
import script from './customCanvasAction.js';
import view from './customCanvasAction.vue';

export default {
  name: 'canvas-action',
  category: 'canvas',        // Required for canvas actions
  icon: 'script-text',       // MDI icon for the toolbar
  script: script,
  view: view
};
```




