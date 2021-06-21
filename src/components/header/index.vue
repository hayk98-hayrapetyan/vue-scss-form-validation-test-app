<template>
  <nav>
    <router-link to="/" tag="div" class="nav-brand">
      <AppLogo />
    </router-link>
    <BurgerMenu @toggle="toggle" />
    <transition name="slide">
      <ul v-if="show">
        <NavLink
          v-for="link in links"
          :key="link.name"
          :link="link"
        />
      </ul>
    </transition>
  </nav>
</template>

<script>
import AppLogo from "@/components/ui/AppLogo";
import NavLink from "@/components/header/components/NavLink";
import BurgerMenu from "@/components/header/components/BurgerMenu";

export default {
  components: { AppLogo, NavLink, BurgerMenu },
  data: () => ({
    links: [
      { name: 'Home', slug: '/' },
      { name: 'About Us', slug: '/about' },
      { name: 'Wish List', slug: '/wish-list' },
      { name: 'Cart', slug: '/cart' },
      { name: 'Sign In', slug: '/login' },
    ],
    show: true,
    resize: null
  }),
  methods: {
    toggle(){
      this.show = !this.show;
    },
    checkSize(){
      if(innerWidth < 600){
        return this.show = false
      }
      return this.show = true
    }
  },
  created() {
    this.checkSize();
    this.resize = window.addEventListener('resize', this.checkSize)
  }
}
</script>>

<style lang="scss" scoped>
nav {
  padding: 10px 40px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  background: #e8e8e8;
  .nav-brand {
    height: 50px;
    cursor: pointer;
  }
  ul {
    display: flex;
  }
  @include mQ(978px){
    padding: 10px 20px;
  }
  @include mQ(600px){
    position: relative;
    .nav-brand {
      height: 40px;
    }
    ul {
      //display: none;
      position: absolute;
      right: 0;
      top: 100%;
      background: inherit;
      width: 100%;
      display: block;
      text-align: right;
      z-index: 10;
      padding-right: 20px;
      //animation: slide 300ms linear;
    }
  }
}

</style>

