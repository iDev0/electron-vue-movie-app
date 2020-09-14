<template>
<div id="wrapper">

    <h2>NowPlaying</h2>

    <div v-show="loading">
        <img src="../assets/Spinner-1s-200px.gif"/>
    </div>

    <slide :items="nowPlaying" />
</div>
</template>

<script>
import { movieAPI } from '../api'
import slide from "./MainPage/Slide";

export default {
    props : {
        title : {
          type : String,
          required : true
        }
    },
    components: {
      slide
    },
    data : function () {
        return {
            loading : true,
            nowPlaying : [],
        }
    },
  mounted () {
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
h1, h2 {
    color: white;
}
</style>
