<template lang="pug">
  main#app.sm-col-8.mx-auto
    h1 azellagram
    h2.h3 Prepare raw Azellaz product photos for production
    form
      TheFileInput(v-on:file-select="getToWork")
    ul(v-if="files.length > 0")
      li(v-for="file, i in files") {{ file }}
    a(href="https://github.com/brianzelip/azellagram") source
</template>

<script>
// import jimp from "jimp";

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
    }
    // ,
    // handleInputFile(file) {
    //   const vm = this;
    //   const reader = new FileReader();
    //   const convertFileToJson = fileContent => {
    //     vm.csvInput = fileContent;
    //     CSV({ delimiter: ["\t", ","] })
    //       .fromString(fileContent)
    //       .on("header", header => {
    //         vm.setCsvInputHeaders(header);
    //       })
    //       .then(json => {
    //         vm.setCsvAsJson(json);
    //       })
    //       .then(() => {
    //         vm.currentSelector = "TheHeadersSelector";
    //       });
    //   };
    //   if (typeof file === "string") {
    //     convertFileToJson(file);
    //   } else if (typeof file === "object") {
    //     reader.readAsText(file);
    //     reader.onload = function(event) {
    //       convertFileToJson(event.target.result);
    //     };
    //   }
    // }
  }
};
</script>

<style scoped>
img {
  width: 100px;
}
</style>
