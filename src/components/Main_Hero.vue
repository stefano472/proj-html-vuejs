<template>
  <div class="hero">
    <div class="hero__top container flex-row font-09">
      ciao
    </div>
    <div class="hero__body">
      <div class="container">

      </div>
    </div>
    <div class="hero__bottom container flex-row font-09">
      Hero
    </div>
  </div>
</template>

<script>
export default {
    name: "HeroComponent"

}
</script>

<style lang="scss" scoped>
@use '@/style/variables' as *;

.hero{
  // height: 50vh;
  background: $bg-brand;
  background-image: url("@/assets/bg-transparent-3.png");
  &__body {
    height: 37em;
    background-image: url("@/assets/banner-5-2x-scaled.jpg");
    background-position: center;
    background-size: cover;
    background-blend-mode: multiply;
    background-color: rgba($color: #000000, $alpha: 0.3);
  }
  &__bottom {
    height: 10rem;
    // margin-inline-start: 20%;
    justify-content: center;
    background-image: url("@/assets/food-transparent-5.png");
    background-position: bottom left;
    background-size: 14%;
    background-repeat: no-repeat;
    // background-position-x: 17%;
  }
}

</style>