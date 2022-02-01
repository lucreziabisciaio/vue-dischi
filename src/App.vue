<template>
  <div id="app">
    <header-container />
    <search-genre @search="filterGenre" />
    <album-container v-if="loader" :albumList="albumListFiltered" />
    <loader-box v-else />
  </div>
</template>

<script>
import axios from 'axios'
import HeaderContainer from './components/HeaderContainer.vue'
import AlbumContainer from './components/AlbumContainer.vue'
import LoaderBox from './components/LoaderBox.vue'
import SearchGenre from './components/SearchGenre.vue'

export default {
  name: 'App',
  components: {
    HeaderContainer,
    AlbumContainer,
    LoaderBox,
    SearchGenre,

  },
  data() {
    return {
      albumList: [],
      loader: false,
      albumListFiltered: [],
    }
  },
  methods: {
    filterGenre(k) {
      this.albumListFiltered = this.albumList.filter((album) => {
        return album.genre.toLowerCase().includes(k);
      })
    }
  },
  mounted() {
    setTimeout( () => {
      axios.get('https://flynn.boolean.careers/exercises/api/array/music').then((response) => {
      this.albumList = response.data.response
      this.albumListFiltered = response.data.response
      this.loader = true
      })
    }, 1000)
  }
}
</script>

<style lang="scss">
@import './style/main.scss'
</style>
