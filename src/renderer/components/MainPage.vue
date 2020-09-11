<template>
    <div id="wrapper">
        <h1>HELLO MOVIE APP!!</h1>
        <ul v-for="movie in nowPlaying" :key="movie.id">
          <li>영화제목 : {{ movie.title }}, 영화평점 : {{ movie.vote_average }}</li><br/>
          <img :src="poster(movie.poster_path)" width="300" height="300"/>
        </ul>
    </div>
</template>

<script>
import { movieAPI, apiImage } from '../api'

export default {
  data : function () {
    return { nowPlaying : [] }  
  },
  methods : {
    poster : function(path) {
      return apiImage(path)
    }
  }, 
  mounted () {
    movieAPI.nowPlaying()
      .then(([result, error]) => {
        console.log(result);
        this.nowPlaying = result
      });
  }
}
</script>

<style>

</style>