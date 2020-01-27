<template lang="pug">
  main#app.sm-col-8.mx-auto.p2
    h1 azellagram
    h2.h3 Prepare raw Azellaz product photos for production
    form
      TheFileInput(v-on:file-select="getToWork")
    ul(v-if="files.length > 0")
      li(v-for="file, i in files") {{ file }}
    a(href="https://github.com/brianzelip/azellagram") source
</template>

<script>
/* eslint-disable */
import Jimp from "jimp/es";

import TheFileInput from "./components/TheFileInput.vue";

export default {
  name: "app",
  components: {
    TheFileInput
  },
  data() {
    return {
      files: []
    };
  },
  methods: {
    getToWork(fileList) {
      const vm = this;

      if (fileList.length > 0) {
        const files = [];
        fileList.forEach(f => {
          files.push(f.name);
        });
        vm.$set(vm, "files", files);
      }

      fileList.forEach((file, i) => {
        console.log("fileList[i].path::::::", fileList[i].path);
        Jimp.read(`${fileList[i].path}`, (err, img) => {
          if (err) throw err;
          img
            .resize(256, 256) // resize
            .quality(60) // set JPEG quality
            .greyscale() // set greyscale
            .write("lena-small-bw.jpg"); // save
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
