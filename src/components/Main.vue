<template>
  <div>
    <Jumbo />
    <Browse />
    <Testimonials />
    <NewProduct />
  </div>
</template>

<script>
import Jumbo from '@/components/Main_Jumbo.vue'
import Browse from '@/components/Main_Browse.vue'
import Testimonials from '@/components/Main_Testimonials.vue'
import NewProduct from '@/components/Main_NewProduct.vue'


export default {
    name: "MainComponent",
    components: {
      Jumbo,
      Browse,
      Testimonials,
      NewProduct
    }

}
</script>

<style lang="scss" scoped>

</style>