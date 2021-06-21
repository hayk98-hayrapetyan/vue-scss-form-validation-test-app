<template>
  <div class="view">
    <a
      v-for="view in views"
      :key="view.name"
      :class="{active: active === view.name}"
      @click="active = view.name; $emit('view', view.name)"
    >
      <i :class="view.icon"></i>
    </a>
  </div>
</template>

<script>
export default {
  name: 'AppView',
  data: () => ({
    active: 'grid',
    views: [
      { name: 'list', icon: 'fa fa-list' },
      { name: 'grid', icon: 'fa fa-th' }
    ]
  })
}
</script>

<style lang="scss" scoped>
.view {
  background: #5796B2;
  padding: 15px 40px;
  display: flex;
  justify-content: flex-end;
  a {
    margin-left: 30px;
    padding: 10px;
    background: #4986A1;
    cursor: pointer;
    transition: all .3s;
    &.active {
      background: $roze;
    }
    i {
      color: white;
      font-size: 25px;
    }
  }
  @include mQ(978px){
    padding: 10px 20px;
  }
  @include mQ(500px){
    display: none!important;
  }
}
</style>