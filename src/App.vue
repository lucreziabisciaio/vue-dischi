<template>
  <div id="app">
    <header-container />
    <search-genre @search="filterGenre" :genreOptions="getGenreValue" />
    <search-artist @search="filterArtist" :artistOptions="getArtistValue" />
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
import SearchArtist from './components/SearchArtist.vue'

export default {
  name: 'App',
  components: {
    HeaderContainer,
    AlbumContainer,
    LoaderBox,
    SearchGenre,
    SearchArtist,

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
        return album.genre.toLowerCase() === k || k === 'all';
      })
    },
    filterArtist(x) {
      this.albumListFiltered = this.albumList.filter((album) => {
        return album.author.toLowerCase() === x || x === 'all';
      })
    },
  },
  computed: {
    getGenreValue() {
      const genreValues = [];
      this.albumList.forEach((element) => {
        if(!genreValues.includes(element.genre.toLowerCase())) {
          genreValues.push(element.genre.toLowerCase())
        }
      })
      return genreValues;
    },
    getArtistValue() {
      const artistValues = [];
      this.albumList.forEach((element) => {
        if(!artistValues.includes(element.author.toLowerCase())) {
          artistValues.push(element.author.toLowerCase())
        }
      })
      return artistValues;
    },
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
