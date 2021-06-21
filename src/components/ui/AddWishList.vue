<template>
  <div @click="add">
    <i
        class="fa fa-heart"
        :class="{selected: favorite}"
    ></i>
  </div>
</template>

<script>
export default {
  name: "AddWishList",
  props: {
    favorite: {
      type: Boolean
    }
  },
  model: {
    prop: 'favorite',
    event: 'click'
  },
  methods: {
    add(){
      this.$emit('click', !this.favorite)
    }
  }
}
</script>

<style lang="scss" scoped>
div {
  width: 50px;
  height: 50px;
  background: white;
  border-radius: 50%;
  display: flex;
  justify-content: center;
  align-items: center;
  position: absolute;
  right: 10px;
  top: 10px;
  z-index: 5;
  cursor: pointer;
  i {
    font-size: 22px;
    transition: all .3s;
    color: $gray;
    &.selected {
      color: $roze;
    }
  }
}
</style>