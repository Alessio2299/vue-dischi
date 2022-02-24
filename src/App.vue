<template>
  <div id="app">
    <HeaderPage @changedGenre="searchGenre" @changedAuthor="searchAuthor" :options="genreList" :optionsAuthor="authorList" />
    <MainPage @genre="optionGenre" @author="optionAuthor" :value="valueOption" :valueAuthor="valueOptionAuthor"/>
  </div>
</template>

<script>
import HeaderPage from './components/Headerpage.vue';
import MainPage from './components/MainPage.vue'

export default {
  name: 'App',
  data(){
    return{
      genreList: [],
      authorList: [],
      valueOption: "All",
      valueOptionAuthor: "All"
    }
  },
  components: {
    HeaderPage,
    MainPage
  },
  methods: {
    optionGenre(genre){
      this.genreList = genre;
    },
    optionAuthor(author){
      this.authorList = author;
    },
    searchGenre(value){
      this.valueOption = value;
    },
    searchAuthor(value){
      this.valueOptionAuthor = value;
    }
  }
}
</script>

<style lang="scss">
  @import "./assets/style/general.scss"
</style>
