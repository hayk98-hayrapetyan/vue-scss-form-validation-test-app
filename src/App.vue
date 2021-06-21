<template>
  <div>
    <AppHeader />
    <RouterView />
  </div>
</template>

<script>
import AppHeader from '@/components/header';

export default {
  name: 'App',
  components: {
    AppHeader
  }
}
</script>

<style lang="scss">

</style>
