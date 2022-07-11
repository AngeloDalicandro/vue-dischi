<template>
    <div class="search-bar">
        <div class="filter">
            <label for="genre">Genere</label>

            <select v-model="selectedGenre" @change="selectGenre(selectedGenre)" name="genre-selector" id="genre">
                <option  v-for="genre, index in genres" :key="index" :value="genre">{{genre}}</option>
            </select>
        </div>
    </div>
</template>

<script>
export default {
    name: "SearchBar",
    data() {
        return {
            selectedGenre: "All",
        }
    },
    props: {
        genres: Array
    },
    methods: {
        selectGenre(selection) {
            this.$emit('genreSelection', selection);
        }
    }
}
</script>

<style lang="scss" scoped>
    .search-bar {
        margin-bottom: 2rem;
        display: flex;
        justify-content: center;

        label {
            color: white;
            margin-right: 1rem;
        }

        select {
            padding: 0.25rem 0.5rem;
        }
    }
</style>