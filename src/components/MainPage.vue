<template>
  <main>
    <div class="container">
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
    .container{
    display: flex;
    justify-content: space-between;
    width: 80%;
    flex-wrap: wrap;
    margin: auto;
    padding: 50px 0; 
   }
  }
</style>