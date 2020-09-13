<template>
    <div id="wrapper">
        <h1>
            {{ title.length > 0 ? title : '타이틀을 찾을 수 없습니다. :(' }}
        </h1>
        <!-- 4번 영화데이터 for문 돌리기 -->
        <ul v-for="movie in nowPlaying" :key="movie.id">
            <!-- json data 를 불러옴 -->
          <li>영화제목 : {{ movie.title }}, 영화평점 : {{ movie.vote_average }}</li><br/>
          <img :src="poster(movie.poster_path)" width="400" height="400"/>
        </ul>
    </div>
</template>

<script>
import { movieAPI, apiImage } from '../api'

export default {
  props : {
    title : {
      type : String,
      required : true
    }
  },
  data : function () {
    // 1번 변수 생성
    return {
      nowPlaying : []
    }
  },
  methods : {
    poster : function(path) {
      return apiImage(path)
    }
  }, 
  mounted () {
    // 2번 영화 데이터 호출
    movieAPI.nowPlaying()
      .then(([result, error]) => {
        console.log(result);
        // 3번 생성한 1번 변수에 영화 데이터 저장
        this.nowPlaying = result
      });
  }
}
</script>

<style>

</style>