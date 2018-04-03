<template>
  <div>
    <carousel>
      <carousel-slide v-for="n in slides" :key="n.id">
        <div style="text-align:center;background-color:rgba(233, 78, 78, 0.1);color:white;">Slide {{ n }}</div>
        <img :src="'https://placeimg.com/510/300/any'">
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
