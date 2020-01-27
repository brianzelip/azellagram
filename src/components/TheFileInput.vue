<template lang="pug">
  div
    label(for="file-selector") Select image file(s)
    input.block.col-12.mb1.field(type="file" multiple id="file-selector" v-on:change="fileSelect")
</template>

<script>
export default {
  name: "TheFileInput",
  methods: {
    fileSelect(e) {
      this.$emit("file-select", e.target.files);
    }
  }
};
</script>
