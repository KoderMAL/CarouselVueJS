<template>
  <div class="todoapp carousel">
    <slot></slot>
    <button class="carousel__nav carousel__next" @click.prevent="next">Next</button>
    <button class="carousel__nav carousel__prev" @click.prevent="prev">Previous</button>
    <div class="carousel__pagination">
      <button v-for="n in slidesCount" :key="n.id" @click="goto(n-1)" :class="{active: n-1 == index}"></button>
    </div>
  </div>
</template>

<script>
export default {
  data () {
    console.log(this.$children)
    return {
      index: 0,
      slides: [],
      direction: null
    }
  },
  mounted () {
    this.slides = this.$children
    this.slides.forEach((slide, i) => {
      slide.index = i
    })
  },
  computed: {
    slidesCount () { return this.slides.length }
  },
  methods: {
    next () {
      this.index++
      this.direction = 'right'
      if (this.index >= this.slidesCount) {
        this.index = 0
      }
    },
    prev () {
      this.index--
      this.direction = 'left'
      if (this.index < 0) {
        this.index = this.slidesCount - 1
      }
    },
    goto (index) {
      this.direction = index > this.index ? 'right' : 'left'
      this.index = index
    }
  }
}
</script>

<style>
img {
  width: 100%;
}
.carousel {
  position: absolute;
  overflow: hidden;
}

.carousel__nav {
  top: 50%;
  position: absolute;
  left: 10px;
  width: 63px;
  margin-top: -31px;
  height: 63px;
  background: lightcoral;
  color: white;
}

.carousel__nav.carousel__next {
  right: 10px;
  border-radius: 50%;
  left: auto;
}

.carousel__nav.carousel__prev {
  left: 10px;
  border-radius: 50%;
  right: auto;
}

.carousel__pagination {
  position: absolute;
  bottom: 10px;
  left: 0;
  right: 0;
  text-align: center;
}

.carousel__pagination button {
  display: inline-block;
  width: 10px;
  height: 10px;
  background-color: #000;
  opacity: 0.8;
  border-radius: 10px;
  margin: 0 2px;
}

.carousel__pagination button.active {
  background-color: #fff;
}

button:hover {
  opacity: 0.9;
}

</style>
