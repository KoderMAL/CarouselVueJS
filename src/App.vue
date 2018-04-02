<template>
  <div>
    <carousel>
      <carousel-slide v-for="n in slides">
        <div>Slide {{ n }}</div>
        <img :src="'http://lorempixel.com/400/200/' + n">
      </carousel-slide>
    </carousel>
   <todos></todos>
  </div>
</template>

<script>
import Todos from './components/Todos'
import Carousel from './components/Carousel/Carousel.vue'
import CarouselSlide from './components/Carousel/CarouselSlide.vue'

export default {
  name: 'app',
  data () {
    return {
      slides: 5
    }
  },
  components: {
    Todos,
    Carousel,
    CarouselSlide
  }
}
</script>
