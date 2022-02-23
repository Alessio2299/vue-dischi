<template>
  <main>
    <LoadingMain  v-if="listAlbum.length < 10" :text="textLoading"/>
    <div class="container" v-if="listAlbum.length == 10">
      <DiskMain v-for="(album, index) in listAlbum" :key="(index)" :album="album"/>
    </div>
  </main>
</template>

<script>
  import DiskMain from "./DiskMain.vue";
  import LoadingMain from "./LoadingMain.vue";

  const axios = require('axios');
  export default {
    name: "MainPage",
    data(){
      return{
        listAlbum: [],
        text: "loading...",
        textLoading: "",
        loading: null
      }
    },
    components: {
      DiskMain,
      LoadingMain
    },
    methods:{
      getAlbum(){
        axios.get('https://flynn.boolean.careers/exercises/api/array/music')
        .then((response) => {
          this.listAlbum = response.data.response;
          console.log(this.listAlbum)
        })
      },
      singleLetter(){
          let i = 0;
        this.loading = setInterval(() => {
          this.textLoading += this.text[i];
          i++;
          if(this.textLoading.length == this.text.length){
            this.textLoading = "";
            i = 0;
          }
        },500)
      }
    },
    mounted(){
      this.getAlbum();
      this.singleLetter();
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