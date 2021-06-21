<template>
  <li>
    <router-link :to="link.slug">
      {{ link.name }}
    </router-link>
  </li>
</template>

<script>
export default {
  name: 'NavLink',
  props: {
    link: {
      type: Object,
      required: true
    }
  }
}
</script>

<style lang="scss" scoped>
li {
  margin: 0 0 0 40px;
  a {
    font-weight: bold;
    color: #2c3e50;
    text-decoration: none;
    transition: all .3s;
    white-space: nowrap;
    &:hover {
      text-decoration: underline;
    }
    &.router-link-exact-active, &:hover {
      color: #42b983;
    }
  }
  @include mQ(600px){
    margin-bottom: 15px;
  }
}
</style>