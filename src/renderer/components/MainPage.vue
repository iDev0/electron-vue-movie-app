<template>
    <div id="wrapper">
        <!-- loading spinner -->
        <div class="loadingio-spinner-spinner-x7ejdclnggh" v-show="loading">
            <div class="ldio-kqajj5wfe5">
                <div></div><div></div><div></div><div></div><div></div><div></div><div></div><div></div><div></div><div></div><div></div><div></div>
            </div>
        </div>

        <ul v-for="movie in nowPlaying" :key="movie.id" v-show="!loading">
            <transition name="fade">
                <li style="list-style: none">
                    <div>
                        <Poster :path="movie.poster_path" width="300" height="300" />
                        <p> 영화제목 : {{ movie.title }}</p>
                        <p>영화평점 : {{ movie.vote_average }} </p>
                    </div>
                </li>
            </transition>
        </ul>
    </div>
</template>

<script>
import { movieAPI } from '../api'
import Poster from "./MainPage/Poster";

export default {
  props : {
    title : {
      type : String,
      required : true
    }
  },
  components: { Poster },
  data : function () {
    // 1번 변수 생성
    return {
        loading : true,
        nowPlaying : []
    }
  },
  mounted () {
    // 2번 영화 데이터 호출
    movieAPI.nowPlaying()
      .then(([result, error]) => {
        console.log(result);
        // 3번 생성한 1번 변수에 영화 데이터 저장
          this.nowPlaying = result
          this.loading = false
      });
  }
}
</script>

<style>
ul {
    float: left;
}
ul li {
    height: 400px;
    border: 1px solid;
    padding: 10px;
    border-radius: 15px;
}

.fade-enter-active, .fade-leave-active {
    transition: opacity .5s;
}
.fade-enter, .fade-leave-to /* .fade-leave-active below version 2.1.8 */ {
    opacity: 0;
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