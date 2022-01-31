<template>
  <div id="app">
    <header-container />
    <album-container v-if="loader" :albumList="albumList" />
    <loader-box v-else />
  </div>
</template>

<script>
import axios from 'axios'
import HeaderContainer from './components/HeaderContainer.vue'
import AlbumContainer from './components/AlbumContainer.vue'
import LoaderBox from './components/LoaderBox.vue'

export default {
  name: 'App',
  components: {
    HeaderContainer,
    AlbumContainer,
    LoaderBox,

  },
  data() {
    return {
      albumList: [],
      loader: false,

    }
  },
  mounted() {
    setTimeout( () => {
      axios.get('https://flynn.boolean.careers/exercises/api/array/music').then((response) => {
      this.albumList = response.data.response
      this.loader = true
      })
    },2000)
  }
}
</script>

<style lang="scss">
@import './style/main.scss'
</style>
