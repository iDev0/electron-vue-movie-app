<template>
<div id="wrapper">


    <div v-show="loading">
        <img src="../assets/Spinner-1s-200px.gif" alt="loading image"/>
    </div>

    <h2>NowPlaying</h2>
    <slide :items="nowPlaying" />
    <h2>Popular</h2>
    <slide :items="popular" />
    <h2>Upcoming</h2>
    <slide :items="upcoming" />
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
            popular : [],
            upcoming : []
        }
    },
  mounted () {
    movieAPI.nowPlaying()
      .then(([result, error]) => {
          if (error) throw error
          this.nowPlaying = result
      }).catch((error) => console.log(error))

    movieAPI.popular()
      .then(([result, error]) => {
          if (error) throw error
          this.popular = result
      }).catch((error) => console.log(error))

    movieAPI.upcoming()
        .then(([result, error]) => {
            if (error) throw error
            this.upcoming = result
        })
        .catch((error) => console.log(error))
      this.loading = false
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
