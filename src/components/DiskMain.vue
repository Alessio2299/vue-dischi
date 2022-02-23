<template>
  <div>
    <div class="card">
        <img :src="album.poster" :alt="album.title">
        <h1></h1>
    </div>
  </div>
</template>

<script>
export default {
  name: "DiskMain",
  props: {
    album: Object
  }
}
</script>

<style lang="scss" scoped>
  .card{
    width: 200px;
    height: 200px;
    border-radius: 50%;
    position: relative;
    margin-bottom: 80px;
    img{
      width: 100%;
      height: 100%;
      border-radius: 50%;
    }
    &::before{
      content: "";
      width: 50px;
      height: 50px;
      border-radius: 50%;
      position: absolute;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%);
      background-color: rgb(30, 45, 59);
    }
  }
</style>