<template>
    <div>
        <select v-model="keywordGenre" @change="$emit('search', keywordGenre)">
            <option disabled value="">Seleziona genere</option>
            <option value="all">All</option>
            <option value="rock">Rock</option>
            <option value="pop">Pop</option>
            <option value="jazz">Jazz</option>
            <option value="metal">Metal</option>
        </select>
    </div>
</template>

<script>
export default {
    data() {
        return {
            keywordGenre: ''
        } 
    },
}
</script>

<style lang="scss" scoped>

</style>