<template>
  <header>
    <img src="../assets/img/logo-spotify.png" alt="Logo Spotify">
    <div>
      <select @change="changedValueGenre" name="genre" v-model="valueOptionGenre" id="genreMusic">
        <option value="All">All</option>
        <option v-for="(option,index) in options" :key="index" :value="option">{{option}}</option>
      </select>
      <select @change="changedValueAuthor" name="author" v-model="valueOptionAuthor" id="genreMusic">
        <option value="All">All</option>
        <option v-for="(option,index) in optionsAuthor" :key="index" :value="option">{{option}}</option>
      </select>
    </div>
  </header>
</template>

<script>
export default {
  name: 'HeaderPage',
  props: {
    options: Array,
    optionsAuthor: Array
  },
  data(){
    return{
      valueOptionGenre: "All",
      valueOptionAuthor: "All"
    }
  },
  methods:{
    changedValueGenre(){
      this.$emit("changedGenre", this.valueOptionGenre);
    },
    changedValueAuthor(){
      this.$emit("changedAuthor",this.valueOptionAuthor);
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
