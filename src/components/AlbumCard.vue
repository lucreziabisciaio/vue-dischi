<template>
    <div class="album_card text-center p-3 m-3">
        <div class="album_poster">
            <img class="w-100" :src="album.poster" alt="">
        </div>

        <div class="album_info text-break">
            <div class="album_title text-white fs-4 text-uppercase my-2">{{ album.title }}</div>
            <div class="author text-white">{{ album.author }}</div>
            <div class="year text-white">{{ album.year }}</div>
        </div>
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
.album_card {
    width: 200px;
    height: 350px;
    max-height: 350px;
    overflow: hidden;
    background-color: rgba(255, 255, 255, 0.1);
}

.album_poster {
    max-height: 150px;
    overflow: hidden;
}
</style>