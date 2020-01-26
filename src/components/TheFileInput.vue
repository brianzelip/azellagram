<template lang="pug">
  div
    label(for="file-selector") Select image(s)
    input.block.col-12.mb1.field(type="file" multiple id="file-selector" v-on:change="updateFiles")
    p Files: {{ files }}
</template>

<script>
export default {
  name: 'TheFileInput',
  data() {
    return {
      files: []
    };
  },
  methods: {
    updateFiles(e) {
      const fList = e.target.files;
      const files = [];

      fList.forEach(f => {
        files.push(f.name);
      });

      this.$set(this, 'files', files);

      this.$emit('file-input', this.files);
    }
  }
};
</script>
