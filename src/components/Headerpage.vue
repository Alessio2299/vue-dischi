<template>
  <header>
    <img src="../assets/img/logo-spotify.png" alt="Logo Spotify">
    <select @change="changedValue" name="genre" v-model="valueOption" id="genreMusic">
      <option value="All">All</option>
      <option v-for="(option,index) in options" :key="index" :value="option">{{option}}</option>
    </select>
  </header>
</template>

<script>
export default {
  name: 'HeaderPage',
  props: {
    options: Array
  },
  data(){
    return{
      valueOption: "All",
    }
  },
  methods:{
    changedValue(){
      this.$emit("changedGenre", this.valueOption)
    }
  }
}

</script>
 
<style scoped lang="scss">
  header{
    background-color: rgb(45, 58, 70);
    display: flex;
    justify-content: space-between;
    align-items: center;
    img{
      width: 80px;
      padding: 10px;
    }
    select{
      margin-right: 30px;
      width: 100px  ;
    }
  }
</style>
