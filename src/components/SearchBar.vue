<template>
    <div class="search-bar">
        <div class="filter-by-genre">
            <label for="genre">Genere</label>

            <select v-model="selectedGenre" @change="selectGenre(selectedGenre)" name="genre-selector" id="genre">
                <option  v-for="genre, index in genres" :key="index" :value="genre">{{genre}}</option>
            </select>
        </div>

        <div class="filter-by-artist">
            <label for="artist">Artista</label>

            <select v-model="selectedArtist" @change="selectArtist(selectedArtist)" name="artist-selector" id="artist">
                <option  v-for="artist, index in artists" :key="index" :value="artist">{{artist}}</option>
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
            selectedArtist: "All"
        }
    },
    props: {
        genres: Array,
        artists: Array
    },
    methods: {
        selectGenre(selection) {
            this.$emit('genreSelection', selection);
        },
        selectArtist(selection) {
            this.$emit('artistSelection', selection);
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