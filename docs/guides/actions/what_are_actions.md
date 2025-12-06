---
sidebar_label: 'What are actions?'
sidebar_position: 1
---

Custom actions allow you to extend and customize the behavior of the package by adding your own logic, UI interactions, and workflow triggers. This section describes how actions work, how they interact with the meeting room, and how to create and register them within a project.

## Overview
Custom actions offer a powerful and flexible way to introduce custom functionality into a meeting room environment. They can be used to:
- Trigger custom business logic
- Inject UI interactions
- Extend default behaviors
- Integrate third-party tools or services

An action can affect one or multiple participants inside the meeting room. Each action runs through a two-step workflow:

### Client → Server Request (Validation Layer)
The action is initiated from the client (usually through a Vue component).
The request is sent to the server, where it can be validated—checking permissions, user roles, room state, or any custom conditions.

### Server → Clients Execution (Action Handler)
If the server approves the request, the action is executed on the target user's device(s).
This execution layer is implemented as a plain JavaScript module, independent from the Vue layer.

*This separation ensures:*
- secure validation of user-initiated actions
- consistent behavior across all connected clients
- clear distinction between UI logic and execution logic



