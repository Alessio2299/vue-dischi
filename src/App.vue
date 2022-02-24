<template>
  <div id="app">
    <HeaderPage @changedGenre="search" :options="genreList"/>
    <MainPage @genre="optionGenre" :value="valueOption"/>
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
      valueOption: "All"
    }
  },
  components: {
    HeaderPage,
    MainPage
  },
  methods: {
    optionGenre(genre){
      this.genreList = genre
    },
    search(value){
      this.valueOption = value
    }
  }
}
</script>

<style lang="scss">
  @import "./assets/style/general.scss"
</style>
