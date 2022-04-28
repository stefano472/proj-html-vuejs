<template>
    <div v-show="currentSlide === index" 
        @mouseover="$emit('mouseenter')"
        @mouseleave="$emit('mouseout')"
        class="carousel-item flex-column"
    >
        <img :src="userImg(slide.id)" :alt="'avatar-' + slide.id">
        <p>
            <font-awesome-icon class="quote font-30" icon="fa-solid fa-quote-left" />
            <span>{{slide.name}}</span>
        </p>
        <i class="font-09">{{slide.text}}</i>
    </div>
</template>

<script>
export default {
    name: "CarouselItem",
    emits: ['mouseenter', 'mouseout'],
    props: {
        currentSlide: Number,
        index: Number,
        slide: Object
    },
    data() {
        return {
            
        }
    },
    methods: {
        userImg(path) {
        return require(`@/assets/avatar-${path}.jpg`)
      },
    }

}
</script>

<style lang="scss" scoped>
@use '@/style/variables' as *;


.carousel-item {
    border-radius: 50%;
    padding: 2.5rem 0 3.5rem;
    align-items: center;
    justify-content: center;
    margin-inline: auto;
    width: 50%;
    img {
    margin-bottom: 1rem;
    margin-inline: auto;
    border-radius: 50%;
    width: 15rem;
    aspect-ratio: 1/1;
    }
    p {
    position: relative;
    width: fit-content;
    .quote {
        color: $text-subtitle;
        position: absolute;
        top: -2rem;
        left: -4rem;
    }
    }
    i {
        font-weight: 600;
        width: 80%;
        margin-top: 1rem;
        color: $text-subtitle;
    }
}

</style>