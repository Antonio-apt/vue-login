<template>
  <div id="app">
        <div id="nav">
            <router-link v-if="authenticated" to="/login" v-on:click.native="logout()" replace>
              Logout
            </router-link>
        </div>
        <router-view @authenticated="setAuthenticated" />
    </div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      authenticated: false,
      mock: {
        username: 'antonio.neto@madeinweb.com.br',
        password: 'madein1w2',
      },
    };
  },
  mounted() {
    if (!this.authenticated) {
      this.$router.replace({ name: 'Login' });
    }
  },
  methods: {
    setAuthenticated(status) {
      this.authenticated = status;
    },
    logout() {
      this.authenticated = false;
    },
  },
};
</script>

<style lang="scss">

@import url('https://fonts.googleapis.com/css2?family=Roboto:wght@400;500;900&display=swap');

body{
    display: flex;
    justify-content: center;
    background-color:#f7f6f2;
    }

#app {
    font-family: 'Roboto', sans-serif;
    text-align: center;
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

.no-outline:-webkit-autofill,
.no-outline:-webkit-autofill:hover,
.no-outline:-webkit-autofill:focus,
.no-outline:-webkit-autofill:active  {
  -webkit-box-shadow: 0 0 0 30px #ebe6e2 inset !important;
}
.no-outline:focus{
  outline: none !important;
  border-color: #4fbfa6;
  box-shadow: 0 0 10px #4fbfa6;
}

</style>
