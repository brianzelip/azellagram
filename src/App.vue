<template lang="pug">
  main#app.sm-col-8.mx-auto
    h1 azellagram
    h2.h3 Prepare raw Azellaz product photos for production
    form
      TheFileInput(v-on:file-input="updateFiles")
    ul
      li(v-for="file, i in files") {{ file }}
    a(href="https://github.com/brianzelip/azellagram") source
</template>

<script>
import jimp from 'jimp';

import TheFileInput from './components/TheFileInput.vue';

export default {
  name: 'app',
  components: {
    TheFileInput
  },
  data() {
    return {
      files: []
    };
  },
  methods: {
    updateFiles(files) {
      this.$set(this, 'files', files);

      // open a file called "yellow.png"
      this.files.forEach(f => {
        jimp.read(f, function(err, img) {
          if (err) throw err;
          img
            .resize(500, 500) // resize
            .quality(70) // set JPEG quality
            .greyscale() // set greyscale
            .write(`${f}-XXXXXX`); // save
          console.log('Resized !!');
        });
      });
    }
  }
};
</script>

<style scoped>
img {
  width: 100px;
}
</style>
