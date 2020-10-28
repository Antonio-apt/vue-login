<template>
    <main-container>
        <img
            class="login-logo"
            src="../assets/location-marker.svg"
        >
        <input type="text" class= "no-outline input-login" name="username"
        v-model="input.username" placeholder="Username" />
        <input type="password" class= "no-outline input-login" name="password"
        v-model="input.password" placeholder="Password" />
        <submit-button @click-action="login()">
            Sign in
        </submit-button>
        <label v-if=loginError class="error-message">
            Wrong username or password
        </label>
        <label v-if=withoutData class="error-message">
            Username or password is empty
        </label>
    </main-container>
</template>

<script>
import mainContainer from '@/components/MainContainer.vue';
import submitButton from '@/components/SubmitButton.vue';

// @ is an alias to /src

export default {
  name: 'Login',
  components: {
    submitButton,
    mainContainer,
  },
  data() {
    return {
      input: {
        username: '',
        password: '',
      },
      loginError: false,
      withoutData: false,
    };
  },
  methods: {
    login() {
      if (this.input.username !== '' && this.input.password !== '') {
        if (this.input.username === this.$parent.mock.username
        && this.input.password === this.$parent.mock.password) {
          this.$emit('authenticated', true);
          this.$router.replace({ name: 'Home' });
        } else {
          this.loginError = true;
          this.withoutData = false;
        }
      } else {
        this.withoutData = true;
        this.loginError = false;
      }
    },
  },
};
</script>

<style lang="scss" scoped>

    .input-login{
        border: none;
        font-family: 'Roboto', sans-serif;
        min-width: 18.75rem;
        max-width: 21.875rem;
        color: #333230;
        background-color: #ebe6e2;
        margin: 0.3125rem 0.625rem;
        padding: 0.875rem 0.75rem;
        border-radius: 0.3125rem;
        box-sizing: border-box;
        -moz-box-sizing: border-box;
        &::placeholder{
            color: #c9c5bc;
            font-weight: bold;
        }
    }
    .error-message{
        color:#585858;
        font-weight: 500;
    }

    .login-logo{
        margin-bottom: 1.875rem;
    }

</style>
