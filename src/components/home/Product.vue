<template>
  <div class="product" :class="{list: design}">
    <div class="img">
      <AddWishList
          :favorite="product.isFav"
          v-model="product.isFav"
      />
      <ProductImage :img="product.picture" />
    </div>
    <div class="info">
      <h2>{{product.name}}</h2>
      <div class="review">
        <h3>{{product.size}}</h3>
        <AppStars :stars="product.rating" />
      </div>
      <div>
        <div class="price">
          <h1>{{product.price}}</h1>
          <OldPrice
            v-if="product.oldPrice"
            :price="product.oldPrice"
            :save="product.savings"
          />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import AddWishList from "@/components/ui/AddWishList";
import ProductImage from "@/components/ui/ProductImage";
import AppStars from "@/components/ui/AppStars";
import OldPrice from "@/components/ui/OldPrice";

export default {
  components: {
    AddWishList,
    ProductImage,
    AppStars,
    OldPrice
  },
  props: {
    product: {
      type: Object
    },
    design: {
      type: Boolean
    }
  }
}
</script>

<style lang="scss" scoped>
.product {
  width: 31%;
  margin-bottom: 40px;
  box-shadow: 0 0 10px rgba(0,0,0,.2);
  &.list {
   width: 100%;
    display: flex;
    .img {
      max-width: 30%;
    }
    h2, .review {
      margin-bottom: 30px;
    }
  }
  .img {
    width: 100%;
    height: 250px;
    background: #62A3DB;
    position: relative;
  }
  .info {
    padding: 20px 20px 30px;
  }
  h2 {
    color: $purple;
    text-transform: capitalize;
    margin-bottom: 10px;
  }
  .review {
    display: flex;
    align-items: center;
    margin-bottom: 10px;
    h3 {
      margin-right: 5px;
    }
  }
  .price {
    display: flex;
    align-items: baseline;
  }
  h1 {
    font-size: 30px;
    color: $purple;
    font-weight: bold;
    margin-right: 5px;
  }
  @include mQ(978px){
    width: 32%;
    margin-bottom: 20px;
    .img {
      height: 200px;
    }
  }
  @include mQ(787px){
    width: 48%;
    &.list {
      .img {
        max-width: 40%;
      }
      h2, .review {
        margin-bottom: 10px;
      }
    }
    .img {
      height: 170px;
    }
  }
  @include mQ(500px){
    max-width: 340px;
    margin: 0 auto 20px;
    width: 100%;
    &.list {
      display: block;
      .img {
        max-width: unset;
      }
      h2, .review {
        margin-bottom: 10px;
      }
    }
    .img {
      height: 200px;
    }
  }
}
</style>