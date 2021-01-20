# vue-google-auth
Super quick Google Firebase sign-in example, based on Vue 3.

Project created with Vue 3 CLI and added Firebase:

```
vue create project-name
npm i firebase -S
```

App.vue checks if the user is signed in through Google:
- Displays a "loading" text while establishing connections
- If the user is logged in, show display name and logout button
- If the user is not logged, display a login button that authenticates through redirection

Remember to set up and enable Google authentication in the Firebase console on Google.

Configuration stored in .env file, copy settings and save as .env.local. Used in firebase.js.

Environment variables require `VUE_APP` prefix to be loaded in Vue 3.

## Project setup
```
npm install
```

### Compiles and hot-reloads for development
```
npm run serve
```

### Compiles and minifies for production
```
npm run build
```

### Run your unit tests
```
npm run test:unit
```

### Lints and fixes files
```
npm run lint
```

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).
