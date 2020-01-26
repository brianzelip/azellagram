<template lang="pug">
  main#app
    h1 azellagram
    h2.h3 Prepare raw Azellaz product photos for production
    form.sm-col-6.mx-auto
      TheFileInput
    a(href="https://github.com/brianzelip/azellagram") source
</template>

<script>
import TheFileInput from './components/TheFileInput.vue';

export default {
  name: 'app',
  components: {
    TheFileInput
  }
};
</script>

<style scoped>
main {
  text-align: center;
}
img {
  width: 100px;
}
</style>
