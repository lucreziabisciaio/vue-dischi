<template>
    <div class="container d-flex justify-content-center">
        <select
            class="text-white mx-2 mt-3 rounded bg-transparent"
            v-model="keywordGenre"
            @change="$emit('selectGenre', keywordGenre)">
            
            <option disabled value="">Seleziona genere</option>
            <option value="all">All</option>
            <option 
                v-for="(genre, i) in genreOptions"
                :key="i"
                :value="genre">
            
                {{genre}}
                </option>
        </select>

        <select
            class="text-white mx-2 mt-3 rounded bg-transparent"
            v-model="keywordAuthor"
            @change="$emit('selectArtist', keywordAuthor)">
            
            <option disabled value="">Seleziona artista</option>
            <option value="all">All</option>
            <option 
                v-for="(author, i) in artistOptions"
                :key="i"
                :value="author">
            
                {{author}}
                </option>
        </select>
    </div>
</template>

<script>
export default {
    data() {
        return {
            keywordGenre: 'all',
            keywordAuthor: 'all',
        } 
    },
    props: {
        genreOptions: Array,
        artistOptions: Array,
    },
}
</script>

<style lang="scss" scoped>

option {
    color: #1e2d3b;
}

</style>