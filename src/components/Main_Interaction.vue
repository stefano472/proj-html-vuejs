<template>
  <div>
    <div class="testimonials">
      <div class="container">
        <h2 class="font-25">User testimonials</h2>
        <carousel :per-page="3"
                  :autoplay="true"
                  :autoplayTimeout="5000"
                  :loop="true"
                  :speed="1500"
  
                  class="carousel"
        >
          <slide class="card flex-column" v-for="testimonial in userTestimonials" :key="testimonial.id" >
            <img :src="userImg(testimonial.id)" :alt="'avatar-' + testimonial.id">
            <p>
              <font-awesome-icon class="quote font-30" icon="fa-solid fa-quote-left" />
              <span>{{testimonial.name}}</span>
            </p>
            <i class="font-09">{{testimonial.text}}</i>
          </slide>
        </carousel>
      </div>
    </div>
    <div class="tips container">
      <div class="newsletter">
        <div class="container">
          <div class="wrapper">
            <h2 class="font-25">Join our newsletter</h2>
            <p class="font-09">Volutpat vel turpis nulla lorem sed semper. Aliquam sagittis sem libero viverra vehicula nullam ut nisl.</p>
            <div class="subscribe flex-row">
              <input v-model="inputEmail" type="text" class="input" placeholder="Insert your email ...*">
              <button @click="getInput" class="btn btn__secondary">Subscribe</button>
            </div>
          </div>
        </div>
      </div>
      <h2 class="font-25">Get the best tips & tricks</h2>
      <p class="subtitle">All-time best sellers</p>
      <ul class="flex-row">
        <li v-for="tips in show4TipsTricks" :key="tips.id">
          <img :src="tipsImg(tips.id)" :alt="'blog:'+ tips.id">
          <div class="tips-text">
            <p>{{tips.title}}</p>
            <p class="font-07">{{tips.date}}</p>
          </div>
        </li>
      </ul>
      <button class="btn btn__secondary">read all articles</button>
    </div>
    <div class="product"></div>
  </div>
</template>

<script>
import userTestimonials from "@/data/testimonials.json"
import tipsTrick from "@/data/tips.json"

import { Carousel, Slide } from 'vue-carousel';

export default {
    name: "MainInteraction",
    data() {
      return {
        userTestimonials,
        tipsTrick,
        inputEmail: ''
      }
    },
    components: {
      Carousel,
      Slide
    },
    computed: {
      show4TipsTricks() {
        if(this.tipsTrick.length < 5) {
          return this.tipsTrick
        }
        return this.tipsTrick.slice(0,4)
      }
    },
    methods: {
      userImg(path) {
        return require(`@/assets/avatar-${path}.jpg`)
      },
      tipsImg(path) {
        return require(`@/assets/blog-${path}.jpg`)
      },
      getInput() {
        // this.$emit('getUserInput', this.inputEmail),
        console.log(this.inputEmail)
        this.inputEmail = ''
      }
    }

}
</script>

<style lang="scss" scoped>
@use '@/style/variables' as *;

.testimonials {
  color: $text-title;
  text-align: center;
  background: $bg-brand;
  background-image: url("@/assets/bg-transparent-3.png");
  padding: 5rem 0;
  .carousel {
    .card {
      padding: 3rem 1.5rem 0;
      img {
        margin-bottom: 1rem;
        margin-inline: auto;
        border-radius: 50%;
        width: 8rem;
      }
      p {
        position: relative;
        .quote {
          color: $text-subtitle;
          position: absolute;
          top: -2rem;
          left: 2rem;
        }
      }
      i {
        margin-top: 1rem;
        color: $text-subtitle;
      }
    }
  }
}
.tips {
  position: relative;
  text-align: center;
  padding-top: 22rem;
  .newsletter {
    box-shadow: 0 0 25px 5px rgb(0 0 0 / 20%);
    text-align: left;
    z-index: 50;
    position: absolute;
    top: -5rem;
    width: 100%;
    background-image: url("@/assets/banner-7-2x-scaled.jpg");
    background-size: cover;
    background-blend-mode: multiply;
    background-color: rgba($color: #000000, $alpha: 0.02);
    .wrapper {
      width: min(35rem, 100%);
      padding: 4rem 4rem;
      p {
        padding: 1.75rem 0;
        line-height: 1.8;
      }
      .subscribe {
        gap: 1rem;
        .input {
          border-radius: 2rem;
          height: 2rem;
          width: 20rem;
          padding: 0 1rem;
          border: 0;
          background: $bg-search-bar;
          font-weight: 600;
          &::placeholder {
            color: $text-black;
            font-weight: 400;
          }
          &:focus {
            outline: 0;
          }
        }
      }
    }
  }
  .subtitle {
      color: $text-tertiary;
      padding: 1.5rem 0 3rem;
      font-weight: 600;
    }
  ul {
    margin-bottom: 3rem;
    gap: 2rem;
    li {
      img {
        width: 100%;
      }
      .tips-text {
        text-align: left;
        padding: 1rem 2rem;
        font-weight: 600;
        p:first-child {
          margin-bottom: 0.5rem;
        }
      }
    }
  }
}
</style>