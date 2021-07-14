<template>
  <div id="app">
    <div class="container">
      <Header />
      <Main :characters="characters" />
    </div>
  </div>
</template>

<script>
import axios from 'axios';
import Header from './components/Header.vue';
import Main from './components/Main.vue';

export default {
  name: 'App',
  components: {
    Header,
    Main
  },
  data() {
    return {
      characters: []
    }
  },
  created() {
    axios.get('https://api.sampleapis.com/rickandmorty/characters').then((result) => {
      this.characters = result.data
    })
  }
}
</script>

<style lang="scss">
@import "./style/app.scss"
</style>
