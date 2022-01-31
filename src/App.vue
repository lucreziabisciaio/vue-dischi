<template>
  <div id="app">
    <header-container />
    <album-container :albumList="albumList" />
  </div>
</template>

<script>
import axios from 'axios'
import HeaderContainer from './components/HeaderContainer.vue'
import AlbumContainer from './components/AlbumContainer.vue'

export default {
  name: 'App',
  components: {
    HeaderContainer,
    AlbumContainer,

  },
  data() {
    return {
      albumList: [],

    }
  },
  mounted() {
    axios.get('https://flynn.boolean.careers/exercises/api/array/music').then((response) => {
      this.albumList = response.data.response
    })
  }
}
</script>

<style lang="scss">
@import './style/main.scss'
</style>
