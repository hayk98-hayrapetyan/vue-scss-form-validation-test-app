<template>
  <div class="home">
    <Views @view="changeView" />
    <div class="wrapper">
      <div class="products" :class="{list: list}">
        <Product
          v-for="product in products"
          :key="product.id"
          :product="product"
          :design="list"
        />
      </div>
    </div>
  </div>
</template>

<script>
import Views from '@/components/home/Views';
import Product from "@/components/home/Product";
import products from "@/data/products.json";

export default {
  name: 'Home',
  components: {
    Product,
    Views
  },
  data: () => ({
    products: products,
    list: false
  }),
  methods: {
    changeView: function (e) {
      this.list = e === 'list' ? true : false;
    }
  }
}
</script>

<style lang="scss" scoped>
.wrapper {
  padding: 40px;
  .products {
    display: flex;
    flex-wrap: wrap;
    justify-content: space-between;
    &.list {
      display: block;
    }
  }
  @include mQ(978px){
    padding: 20px;
  }
}
</style>