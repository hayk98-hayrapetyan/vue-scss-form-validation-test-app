<template>
  <button @click="$emit('clicked')">{{text}}</button>
</template>

<script>
export default {
  name: 'BaseButton',
  props: {
    text: {
      type: String,
      default: 'Sent'
    }
  }
}
</script>

<style lang="scss" scoped>
button {
  outline: none;
  border: none;
  background: $roze;
  color: #fff;
  padding: 8px 62px;
  cursor: pointer;
  border-radius: 10px;
  margin-top: 40px;
  @include mQ(600px){
    margin-top: 25px;
  }
}
</style>