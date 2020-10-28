<template>
  <main-container>
    Bem vindo {{email}}!
  </main-container>
</template>

<script>
import mainContainer from '@/components/MainContainer.vue';
// @ is an alias to /src

export default {
  name: 'Home',
  components: {
    mainContainer,
  },
  data() {
    return {
      email: this.$parent.mock.username,
    };
  },
};
</script>
