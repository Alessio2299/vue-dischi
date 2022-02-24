<template>
  <main>
    <LoadingMain  v-if="loadInProgress" :text="textLoading"/>
    <div class="container">
      <DiskMain v-for="(album, index) in listAlbumFiltered" :key="(index)" :album="album"/>
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
        genres: [],
        authors: [],
        text: "loading...",
        textLoading: "",
        loading: null,
        loadInProgress : true,
      }
    },
    props:{
      value: String,
      valueAuthor: String
    },
    computed:{
      listAlbumFiltered(){
        if((this.value == "All") && (this.valueAuthor == "All")){
          return this.listAlbum;
        }else if(this.value == "All"){
          return this.listAlbum.filter(album =>{
            return (album.author.includes(this.valueAuthor));
          });
        }else if(this.valueAuthor == "All"){
           return this.listAlbum.filter(album =>{
            return (album.genre.includes(this.value));
          });
        }else{
          return this.listAlbum.filter(album =>{
            return ((album.author.includes(this.valueAuthor)) && (album.genre.includes(this.value)));
          });
        }
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
          this.loadInProgress = false;
          for(let i = 0; i < this.listAlbum.length; i++){
            this.addGenre(this.genres,this.listAlbum[i].genre, "genre");
            this.addGenre(this.authors,this.listAlbum[i].author, "author");
          }
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
        },200)
      },
      addGenre(array, object, emitName){
        for(let i = 0; i < this.listAlbum.length; i++){
          if(!array.includes(object)){
          array.push(object)
          }
        }
        this.$emit(emitName, array);
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
   height: 100vh;
    .loading{
      text-align: center;
      padding: 80px 0;
    }
    .container{
    display: flex;
    justify-content: flex-start;
    gap: 25px;
    width: 80%;
    flex-wrap: wrap;
    margin: 0 auto;
    padding: 50px 0; 
   }
  }
</style>