<template>
    <div class="album_container container d-flex flex-wrap justify-content-center">
        <div
            v-for="(album, index) in albumList"
            :key="index">

            <album-card :album = "album" />
        </div>
    </div>
</template>

<script>
import AlbumCard from './AlbumCard.vue'

export default {
    components: {
        AlbumCard,

    },
    props: {
      albumList: Array,

    },
    
}
</script>

<style lang="scss" scoped>
.album_container {
    margin-top: 50px;
    margin-bottom: 50px;
}
</style>