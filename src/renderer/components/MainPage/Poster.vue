<template>
    <img :src="imagePath" :width="width" :height="height"/>
</template>

<script>
  import { apiImage } from '../api'

  export default {
    name: "Poster",
    props : {
      path : {
        type : String,
        required : true,
      },
      width : {
        type : Number,
      },
      height : {
        type : Number
      }
    },
    computed : {
      imagePath : function () {
        return apiImage(this.path)
      }
    }
  }
</script>

<style scoped>

</style>