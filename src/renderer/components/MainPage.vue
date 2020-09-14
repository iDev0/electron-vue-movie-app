<template>
    <div id="wrapper">
        <!-- loading spinner -->
        <div class="loadingio-spinner-spinner-x7ejdclnggh" v-show="loading">
            <div class="ldio-kqajj5wfe5">
                <div></div><div></div><div></div><div></div><div></div><div></div><div></div><div></div><div></div><div></div><div></div><div></div>
            </div>
        </div>

        <swiper ref="poster" :options="swiperOptions">
            <swiper-slide v-for="movie in nowPlaying" :key="movie.id">
                <Poster :path="movie.poster_path" width="250" height="250"/>
            </swiper-slide>
            <div class="swiper-pagination" slot="pagination"></div>
            <div class="swiper-button-prev" slot="button-prev"></div>
            <div class="swiper-button-next" slot="button-next"></div>
        </swiper>
    </div>
</template>

<script>
import { movieAPI } from '../api'
import { Swiper, SwiperSlide, directive } from 'vue-awesome-swiper'
import 'swiper/swiper-bundle.css'
import Poster from "./MainPage/Poster";

export default {
  props : {
    title : {
      type : String,
      required : true
    }
  },
  components: {
      Poster,
      Swiper,
      SwiperSlide
  },
    directives : {
      swiper: directive
    },
  data : function () {
    // 1번 변수 생성
    return {
        loading : true,
        nowPlaying : [],
        swiperOptions : {
            slidesPerView: 5,
            spaceBetween: 10,
            slidesPerGroup: 5,
            loop: true,
            loopFillGroupWithBlank: true,
            pagination : {
                el : '.swiper-pagination',
                clickable: true
            },
            navigation: {
                nextEl: '.swiper-button-next',
                prevEl: '.swiper-button-prev'
            }
        }
    }
  },
    computed : {
      swiper() {
        return this.$refs.poster.$swiper
      }
    },
  mounted () {
    this.swiper.slideTo(3, 1000, false)

    // 2번 영화 데이터 호출
    movieAPI.nowPlaying()
      .then(([result, error]) => {
          this.nowPlaying = result
          this.loading = false
      })
  }
}
</script>

<style>
body {
    background: black;
}
p {
    color : white;
}
@keyframes ldio-kqajj5wfe5 {
    0% { opacity: 1 }
    100% { opacity: 0 }
}
.ldio-kqajj5wfe5 div {
    left: 94px;
    top: 48px;
    position: absolute;
    animation: ldio-kqajj5wfe5 linear 1s infinite;
    background: #fe718d;
    width: 12px;
    height: 24px;
    border-radius: 6px / 12px;
    transform-origin: 6px 52px;
}.ldio-kqajj5wfe5 div:nth-child(1) {
     transform: rotate(0deg);
     animation-delay: -0.9166666666666666s;
     background: #fe718d;
 }.ldio-kqajj5wfe5 div:nth-child(2) {
      transform: rotate(30deg);
      animation-delay: -0.8333333333333334s;
      background: #fe718d;
  }.ldio-kqajj5wfe5 div:nth-child(3) {
       transform: rotate(60deg);
       animation-delay: -0.75s;
       background: #fe718d;
   }.ldio-kqajj5wfe5 div:nth-child(4) {
        transform: rotate(90deg);
        animation-delay: -0.6666666666666666s;
        background: #fe718d;
    }.ldio-kqajj5wfe5 div:nth-child(5) {
         transform: rotate(120deg);
         animation-delay: -0.5833333333333334s;
         background: #fe718d;
     }.ldio-kqajj5wfe5 div:nth-child(6) {
          transform: rotate(150deg);
          animation-delay: -0.5s;
          background: #fe718d;
      }.ldio-kqajj5wfe5 div:nth-child(7) {
           transform: rotate(180deg);
           animation-delay: -0.4166666666666667s;
           background: #fe718d;
       }.ldio-kqajj5wfe5 div:nth-child(8) {
            transform: rotate(210deg);
            animation-delay: -0.3333333333333333s;
            background: #fe718d;
        }.ldio-kqajj5wfe5 div:nth-child(9) {
             transform: rotate(240deg);
             animation-delay: -0.25s;
             background: #fe718d;
         }.ldio-kqajj5wfe5 div:nth-child(10) {
              transform: rotate(270deg);
              animation-delay: -0.16666666666666666s;
              background: #fe718d;
          }.ldio-kqajj5wfe5 div:nth-child(11) {
               transform: rotate(300deg);
               animation-delay: -0.08333333333333333s;
               background: #fe718d;
           }.ldio-kqajj5wfe5 div:nth-child(12) {
                transform: rotate(330deg);
                animation-delay: 0s;
                background: #fe718d;
            }
.loadingio-spinner-spinner-x7ejdclnggh {
    width: 200px;
    height: 200px;
    display: inline-block;
    overflow: hidden;
    background: #ffffff;
}
.ldio-kqajj5wfe5 {
    width: 100%;
    height: 100%;
    position: relative;
    transform: translateZ(0) scale(1);
    backface-visibility: hidden;
    transform-origin: 0 0; /* see note above */
}
.ldio-kqajj5wfe5 div { box-sizing: content-box; }
</style>