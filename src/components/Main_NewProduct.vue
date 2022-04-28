<template>
  <div class="container">
    <div class="title">
      <h2 class="font-25">New products arrival</h2>
      <p>Latest products</p>
    </div>
    <ul class="flex-row">
        <li v-for="item in arrayLatestItems" :key="item.name">
          <div v-if="item.onSale.length > 1" class="sale flex-row font-09" >Sale!</div>
          <img :src="item.imgPath" :alt="item.name">
          <h3>{{item.name}}</h3>
          <p v-if="item.onSale.length === 0">{{item.price}}</p>
          <p v-else class="on-sale flex-row">
            <span class="font-07">{{item.price}}</span> 
            <span>{{item.onSale}}</span>
          </p>
        </li>
      </ul>
  </div>
</template>

<script>
import arrayProducts from "@/data/products.json"

export default {
    name: "MainNewProduct",
    data() {
      return {
        arrayProducts,
      }
    },
    computed: {
      arrayLatestItems() {
        // if (this.toggleAllProduct) {
        //   return this.arrayProducts
        // }
        return this.arrayProducts.filter(e => e.newProduct)
      }
    }

}
</script>

<style lang="scss" scoped>
@use '@/style/variables' as *;

.title {
  margin: 4.75rem auto 3rem;
    text-align: center;
}
ul {
    margin-bottom: 4.75rem;
    flex-wrap: wrap;
    gap: 1rem;
    li {
      position: relative;
      text-align: center;
      flex-basis: calc(100% / 3 - 1rem * 2 / 3);
      .sale {
        position: absolute;
        top: 0.5rem;
        left: 0.5rem;
        color: $text-title;
        justify-content: center;
        border-radius: 50%;
        width: 3rem;
        height: 3rem;
        background: $btn-bg-secondary;
      }
      img {
        border-radius: 2px;
        width: 100%;
        padding-bottom: 1rem;
      }
      p {
        color: $text-tertiary;
        margin: 0.7rem auto 1rem;
        &.on-sale {
          justify-content: center;
          gap: 0.2rem;
          span:first-child {
            text-decoration: line-through;
          }
        }
      }
    }
  }
</style>