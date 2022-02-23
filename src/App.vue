<template>
  <div id="app">
    <HeaderPage />
    <MainPage />
  </div>
</template>

<script>
import HeaderPage from './components/Headerpage.vue';
import MainPage from './components/MainPage.vue'

export default {
  name: 'App',
  components: {
    HeaderPage,
    MainPage
  }
}
</script>

<style lang="scss">
  @import "./assets/style/general.scss"
</style>
