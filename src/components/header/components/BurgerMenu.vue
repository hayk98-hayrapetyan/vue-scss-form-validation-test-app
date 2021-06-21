<template>
  <div @click="$emit('toggle')">
    <i class="fa fa-bars"></i>
  </div>
</template>

<script>
export default {
  name: 'BurgerMenu',
}
</script>

<style lang="scss" scoped>
div {
  padding: 5px;
  cursor: pointer;
  display: none;
  i {
    font-size: 25px;
  }
  @include mQ(600px){
    display: block;
  }
}
</style>