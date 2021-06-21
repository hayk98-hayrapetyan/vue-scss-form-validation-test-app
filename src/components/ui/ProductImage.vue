<template>
  <img :src="img" alt="Product image" />
</template>

<script>
export default {
  name: 'Image',
  props: {
    img: {
      type: String
    }
  }
}
</script>

<style lang="scss" scoped>
img {
  height: inherit;
  width: inherit;
  mix-blend-mode: color-burn;
}
</style>