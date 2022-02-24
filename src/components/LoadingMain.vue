<template>
  <div class="loader">
    <img class="green" src="../assets/img/logo-spotify.png" alt="Logo Spotify">
    <img class="gray" src="../assets/img/logo-spotify.png" alt="Logo Spotify">
    <span>{{text}}</span>
  </div>
</template>

<script>
export default {
  name: "loadingMain",
  props: {
    "text": String
  }
}
</script>

<style lang="scss" scoped>
  .loader{
    display: flex;
    align-items: center;
    justify-content: center;
    height: 100%;
    img{
      width: 100px;
      margin-right: 20px;
    }
    span{
      text-transform: uppercase;
      font-size: 30px;
      padding-left: 20px;
      color: #fff;
      width: 100px;
    }
    .gray{
      animation: right 3s linear infinite;
      filter: invert(50%);
      @keyframes right {
        25%{
          transform: translateX(-80px);
          width: 120px;
          z-index: 2;
        }
        50%{
          transform: translateX(-140px);
          width: 100px;
        }
        75%{
          transform: translateX(-20px);
          width: 80px;
        }
      }
    }
    .green{
      animation: left 3s linear infinite;
      @keyframes left {
        25%{
          transform: translateX(80px);
          width: 80px;
        }
        50%{
          transform: translateX(130px);
          width: 100px;
        }
        75%{
          transform: translateX(20px);
          width: 120px;
          z-index: 3;
        }
      }
    }
  }
</style>