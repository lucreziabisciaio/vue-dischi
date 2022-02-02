<template>
    <div>
        <select
            v-model="keywordGenre"
            @change="$emit('search', keywordGenre)">
            
            <option disabled value="">Seleziona genere</option>
            <option value="all">All</option>
            <option 
                v-for="(genre, i) in genreOptions"
                :key="i"
                :value="genre">
            
                {{genre}}
                </option>
        </select>
    </div>
</template>

<script>
export default {
    data() {
        return {
            keywordGenre: 'all'
        } 
    },
    props: {
        genreOptions: Array
    },
}
</script>

<style lang="scss" scoped>

</style>