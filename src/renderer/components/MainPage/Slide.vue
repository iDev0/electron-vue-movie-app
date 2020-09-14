<template>
    <div v-swiper:customSlider="swiperOption">
        <div class="swiper-wrapper">
            <div class="swiper-slide" :key="item.id" v-for="item in items">
                <Poster :path="item.poster_path" width="250" height="300" class="swiper-lazy"/>
                <div class="swiper-lazy-preloader swiper-lazy-preloader-white">
                </div>
            </div>
        </div>
        <div class="swiper-button-prev"></div>
        <div class="swiper-button-next"></div>
    </div>
</template>

<script>
  import { directive } from 'vue-awesome-swiper'
  import 'swiper/dist/css/swiper.min.css'
  import Poster from './Poster'

  // 반응형 처리
  const responseBreakPoints = {
    1024: {
      slidesPerView: 4,
      spaceBetween: 40
    },
    768: {
      slidesPerView: 3,
      spaceBetween: 30
    },
    640: {
      slidesPerView: 2,
      spaceBetween: 20
    },
    320: {
      slidesPerView: 1,
      spaceBetween: 10
    }
  }

  export default {
    name: "slide",
    props : {
      items : {
        type : Array,
        required : true,
      }
    },
    directives : {
      swiper: directive
    },
    components : { Poster },
    data () {
      return {
        swiperOption : {
          slidesPerView: 4,
          spaceBetween: 50,
          slidesPerGroup: 4,
          breakPoints: responseBreakPoints,
          navigation: {
            nextEl: '.swiper-button-next',
            prevEl: '.swiper-button-prev',
          },
          lazy: true,
          loop: true
        },
      }
    },
    mounted() {
      this.customSlider.slideTo(3, 1000, false)
    }
  }
</script>

<style scoped>

</style>