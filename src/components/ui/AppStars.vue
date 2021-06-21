<template>
  <div>
    <i
        v-for="n in stars"
        :key="n"
        class="fa fa-star"
    ></i>
  </div>
</template>

<script>
export default {
  name: 'AppStar',
  props: {
    stars: {
      type: Number
    }
  }
}
</script>

<style lang="scss" scoped>
i {
  color: $roze;
}
</style>