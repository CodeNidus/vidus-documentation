---
sidebar_label: 'How enable canvas?'
sidebar_position: 1
---

## Overview
The Canvas feature provides a dedicated space within Vidus where you can execute custom drawing and annotation actions. This enables functionality such as freehand drawing, text input, shapes, and other interactive visual elements directly on the meeting canvas.

Canvas actions are specifically designed to operate within this visual workspace and are integrated into the canvas toolbar for easy access.

### Enabling the Canvas
By default, the canvas feature is disabled. To activate it, include the following configuration when initializing VidusCreator:

```js
const videoconference = VidusCreator({
    configs: {
      development: {
        canvas: {
          enable: true,
        }
      }
    }
});
```




