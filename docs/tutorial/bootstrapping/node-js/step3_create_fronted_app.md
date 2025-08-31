---
sidebar_label: 'Create a vue fronted'
sidebar_position: 3
---

# Create a Vue.JS fronted app

## A. Preparation
We will use **Vue.js** and the **Vidus Vue package** for the frontend.

Install Vue CLI and create a new project:
```shell
npm install -g @vue/cli
vue create vidus-frontend
cd vidus-frontend
npm i vidus-vue
```

## B. Modify main.js and add Vidus

In main.js, import and configure Vidus:
```js
import { VidusCreator } from "vidus-vue";

const videoconference = VidusCreator();
const app = createApp(App);
app.use(videoconference).mount("#app");
```

## C. Modify App.vue and Use Vidus Components

Add an input field for the username and a button to fetch the token. Also add Vidus Vue  VCRooms and VCRoomJoin components.
```html
<template>
  <input
    v-if="!token"
    id="usernameField"
    v-model="username"
    type="email"
  />
  <button v-if="!token" @click="getUserToken">Get Token</button>

  <div
    v-if="token"
  >
  <VCRooms
    v-if="showRooms"
    @onSelectRoom="setRoomId"
  />
  <div v-else-if="!roomId">Please first create/select a room</div>
  <VCRoomJoin
    v-else
    :room-id="roomId"
    close-url="/"
  />
  </div>
</template>

<script>
import { ref, inject } from 'vue';

export default setup {
    const webrtc = inject('webrtc');
    const token = ref();
    const username = ref('test@test.com');
    const roomId = ref();
    const showRooms = ref(true);


    const getUserToken = () => {
      webrtc.getUserToken(
        (apiToken) => {
          showRooms.value = true;
          token.value = apiToken;
        },
        (error) => { console.log(error); }
      );
    };

    const setRoomId = (room_id) => {
      roomId.value = room_id;
      showRooms.value = false;
    };
}
</script>
```

## D. Override Vidus User Token Helper
1.	By default, the Vidus package’s webrtc.getUserToken method sends an Axios request to /api/videoconference/userToken on the current domain. To override this behavior—such as directing the request to a custom backend and passing a manually entered username—we need to create a secondary helper method and configure it in the Vidus constructor options within main.js. First create a userTokenHelper.js
```shell
touch userTokenHelper.js
```
2.	To customize the token request, create a new method that returns a Promise. The Vidus helper allows you to override its default behavior by passing Axios as an input parameter to your new method. This way, you can modify the request—such as changing the target URL to your Node.js backend endpoint and including a manually entered username in the POST data.
```js
const axiosRequest = (axios) => {
  return new Promise((resolve, reject) => {
    const username = document.getElementById('usernameField').value;
    axios.post('http://localhost:3000/getToken', { username })
      .then(response => resolve(response.data))
      .catch(error => reject('Error: ' + error.response.data.message));
  });
};

export default axiosRequest;
```
3.	To complete the integration, update your main.js file by passing the new custom helper method to the Vidus constructor. This overrides the default token request behavior, ensuring your application uses the modified authentication flow.
```js
import userTokenHelper from "./userTokenHelper";

const videoconference = VidusCreator({
  overrides: {
    helper: {
      userToken: { request: userTokenHelper }
    }
  }
});
```

## E. Run the Frontend App

Start the development server:
```shell
npm run serve
```

Open the app at [http://localhost:8080](http://localhost:8080), enter an email address, fetch a token, create a room, and join it.

Enjoy your Vidus video conferencing experience! 🚀

:::tip
Also you can access to pre-build vidus app by vue & Node.JS in [Github](https://github.com/CodeNidus/vidus-node-vue-quickstart)
:::