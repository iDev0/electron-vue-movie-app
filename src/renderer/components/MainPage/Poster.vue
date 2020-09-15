<template>
    <img :src="imagePath" :width="width" :height="height"/>
</template>

<script>
  import { apiImage } from "../../api";
    // 테스트 주석
  export default {
    name: "Poster",
    props : {
      path : {
        type : String,
        required : true,
      },
      width : {
        type : String,
      },
      height : {
        type : String
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