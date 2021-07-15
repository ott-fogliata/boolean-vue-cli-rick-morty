<template>
  <div id="app">
    <div class="container">
      <Loader v-if="characters.length == 0" />
      <Header @search="searchCharacter" />
      <!--
        searchCharacter(searchString) {
            alert(searchString)
          }
        -->
      <Main :inputSearch="inputSearch" :characters="filteredCharacters" />
    </div>
  </div>
</template>

<script>
import axios from 'axios';
import Header from './components/Header.vue';
import Main from './components/Main.vue';
import Loader from './components/Loader.vue'

export default {
  name: 'App',
  components: {
    Header,
    Main,
    Loader
  },
  data() {
    return {
      characters: [],
      inputSearch: ''
    }
  },
  created() {
    axios.get('https://api.sampleapis.com/rickandmorty/characters')
    .then((result) => {
      this.characters = result.data
      this.searchCharacter('')
    })
  },
  computed: {
    filteredCharacters() {

      // elements è una lista di elementi in cui deve cercare "search"
      function searchIn(search, elements) {
        let exists = false;
        elements.forEach((element) => {
          if(element.toLowerCase().includes(search.toLowerCase())) {
            exists = true;
          }
        });
        return exists;
      }

      if(this.inputSearch.length === 0) {
        return this.characters
      } 

      return this.characters.filter((element) => {

        return searchIn(this.inputSearch, [element.name, element.species, element.origin])

        /* 
        return element.name.toLowerCase().includes(this.inputSearch.toLowerCase()) ||
          element.species.toLowerCase().includes(this.inputSearch.toLowerCase()) ||
          element.origin.toLowerCase().includes(this.inputSearch.toLowerCase()) 
        */

      })
    }
  },
  methods: {
    searchCharacter(searchString) {
      this.inputSearch = searchString.trim()
    }
    /*
    searchCharacter(searchString) {
      this.filteredCharacters = this.characters.filter((element) => {
        return element.name.includes(searchString);  // questo qui è o TRUE o FALSE
      })
    }
    */
  }
}
</script>

<style lang="scss">
@import "./style/app.scss"
</style>
