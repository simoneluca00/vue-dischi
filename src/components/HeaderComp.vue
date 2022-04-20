<template>
  <header>
    <img src="../assets/img/spotify-logo.png" alt="logo Spotify">
  </header>
</template>

<script>
  export default {
    name: 'HeaderComp',

  }
</script>


<style scoped lang="scss">
  header {
    background-color: #2e3a46;
    height: 10vh;
    display: flex;
    align-items: center;

    img {
      height: 70%;
      margin-left: 30px;
    }
  }
</style>