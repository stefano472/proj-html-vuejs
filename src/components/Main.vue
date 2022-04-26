<template>
  <main>
    <Hero />
    <Browse />
    <Testimonials />
    <NewProduct />
  </main>
</template>

<script>
import Hero from '@/components/Main_Hero.vue'
import Browse from '@/components/Main_Browse.vue'
import Testimonials from '@/components/Main_Testimonials.vue'
import NewProduct from '@/components/Main_NewProduct.vue'


export default {
    name: "MainComponent",
    components: {
      Hero,
      Browse,
      Testimonials,
      NewProduct
    }

}
</script>

<style lang="scss" scoped>

</style>