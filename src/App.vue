<template>
  <div v-if="!loading">
    <div v-if="user">
      <span>Welcome {{user.displayName}}!</span><br/>
      <button @click="logout">Log out</button>
      <div id="nav">
        <router-link to="/">Home</router-link> |
        <router-link to="/about">About</router-link>
      </div>
      <router-view/>
    </div>

    <div v-if="!user">
      <h1>Login</h1>
      <button @click="login">Log in with Google</button>
    </div>
  </div>

  <div v-if="loading">
    Loading…
  </div>
</template>

<script>
import { auth, provider } from '@/./firebase';

export default {
  name: 'App',
  data() {
    return {
      loading: true,
      user: null,
    };
  },
  beforeCreate() {
    auth.onAuthStateChanged((user) => {
      if (user) {
        this.user = user;
      } else {
        this.user = null;
      }
      this.loading = false;
    });
  },
  methods: {
    login() {
      auth.signInWithRedirect(provider)
        .then((result) => {
          this.user = result.user;
        })
        .catch((err) => {
          console.error(err);
        });
    },
    logout() {
      auth.signOut()
        .then(() => {
          this.user = null;
        })
        .catch((err) => {
          console.error(err);
        });
    },
  },
};
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 30px;

  a {
    font-weight: bold;
    color: #2c3e50;

    &.router-link-exact-active {
      color: #42b983;
    }
  }
}
</style>
