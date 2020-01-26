<template lang="pug">
  div
    label(for="file-selector") Select image(s)
    input.block.col-12.mb1.field(type="file" multiple id="file-selector")
</template>

<script>
export default {
  name: 'TheFileInput'
};
</script>
