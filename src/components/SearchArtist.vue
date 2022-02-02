<template>
    <div>
        <select
            v-model="keywordAuthor"
            @change="$emit('search', keywordAuthor)">
            
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
            keywordAuthor: 'all'
        } 
    },
    props: {
        artistOptions: Array
    },
}
</script>

<style lang="scss" scoped>

</style>