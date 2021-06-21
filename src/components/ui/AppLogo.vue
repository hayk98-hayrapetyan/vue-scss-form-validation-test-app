<template>
  <img :src="require(`@/assets/img/logo.png`)" alt="logo" />
</template>

<script>
export default {
  name: 'AppLogo'
}
</script>

<style scoped>
img {
  height: inherit;
}
</style>