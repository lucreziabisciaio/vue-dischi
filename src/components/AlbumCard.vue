<template>
    <div class="album_card">
        <div class="album_poster">
            <img :src="album.poster" alt="">
        </div>

        <p class="album_title">{{ album.title }}</p>
        <p class="author">{{ album.author }}</p>
    </div>
</template>

<script>
export default {
    props: {
        album: Object,
    }
}
</script>

<style lang="scss" scoped>

</style>