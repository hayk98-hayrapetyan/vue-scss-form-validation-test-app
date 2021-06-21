<template>
  <div>
    <h6>{{price}}</h6>
    <h6>You Save {{save}}</h6>
  </div>
</template>

<script>
export default {
  name: 'OldPrice',
  props: {
    price: {
      type: String
    },
    save: {
      type: String
    }
  }
}
</script>

<style lang="scss" scoped>
div {
  display: flex;
  h6:first-child {
    text-decoration: line-through;
    color: $gray;
    font-size: 13px;
    margin-right: 5px;
  }
  h6:last-child {
    color: $roze;
    font-size: 13px;
  }
}
</style>