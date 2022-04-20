<template>
  <div id="app">
    <HeaderComp />
    <main>
      <PlaylistComp />
    </main>
  </div>
</template>

<script>
import HeaderComp from './components/HeaderComp.vue'
import PlaylistComp from './components/PlaylistComp.vue'

export default {
  name: 'App',
  components: {
    HeaderComp,
    PlaylistComp,
  }
}
</script>

<style lang="scss">

   * {
     margin: 0;
     padding: 0;
     box-sizing: border-box;
   }

   #app {
     height: 100vh;
     font-family: sans-serif;

      main {
        height: 90vh;
        background-color: #1e2d3b;
        display: flex;
        justify-content: center;
        align-items: center;
      }

   }

</style>
