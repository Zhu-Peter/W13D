<template>
  <div id="app">
    <NowPlaying/>
    <PlayList/>
    <SongList/>
  </div>
</template>

<script>
import NowPlaying from "./components/NowPlaying.vue"
import PlayList from "./components/PlayList.vue"
import SongList from './components/SongList.vue'

export default {
  name: 'App',
  components: {
    NowPlaying, PlayList, SongList
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
