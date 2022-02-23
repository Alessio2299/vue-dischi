<template>
  <main>
    <div class="loading" v-if="listAlbum.length < 10">
      <span>Caricamento</span>
    </div>
    <div class="container" v-if="listAlbum.length == 10">
      <DiskMain v-for="(album, index) in listAlbum" :key="(index)" :album="album"/>
    </div>
  </main>
</template>

<script>
  import DiskMain from "./DiskMain.vue";

  const axios = require('axios');
  export default {
    name: "MainPage",
    data(){
      return{
        listAlbum: []
      }
    },
    components: {
      DiskMain,
    },
    methods:{
      getAlbum(){
        axios.get('https://flynn.boolean.careers/exercises/api/array/music')
        .then((response) => {
          this.listAlbum = response.data.response;
          console.log(this.listAlbum)
        })
      }
    },
    mounted(){
      this.getAlbum();
    }
  }
</script>
<style lang="scss" scoped>
  main{
    background-color: rgb(30, 45, 59);
    height: calc(100vh - 84px);
    .loading{
      text-align: center;
      padding: 80px 0;
    }
    .container{
    display: flex;
    justify-content: space-between;
    width: 80%;
    flex-wrap: wrap;
    margin: 0 auto;
    padding: 50px 0; 
   }
  }
</style>