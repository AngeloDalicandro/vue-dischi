<template>

    <main>
        <SearchBar :genres="genres" @genreSelection="selectGenre" />

        <div class="container">
            <BodyComponent v-for="album, index in filteredAlbums" :key="index"
            :img="album.poster"
            :name="album.title"
            :author="album.author"
            :year="album.year"
            :genre="album.genre"
            />
        </div>
    </main>

</template>

<script>
import axios from 'axios';  
import BodyComponent from './BodyComponent.vue'
import SearchBar from './SearchBar.vue'

export default {
    name: "AppBody",
    components: {
        BodyComponent,
        SearchBar
    },
    data() {
        return {
            url: "https://flynn.boolean.careers/exercises/api/array/music",
            albums: [],
            genres: ["All"],
            selectedGenre: "All"
        }
    },
    computed: {
        filteredAlbums() {
            let albums = [];
            if(this.selectedGenre === "All") {
                albums = this.albums
            } else {
                            this.albums.forEach((album) => {
                if(album.genre === this.selectedGenre) {
                    albums.push(album);
                }
            })
            }

            return albums
        }
    },
    created() {
        this.getAlbums();
    },
    methods: {
        getAlbums() {
            axios.get(this.url).then((response) => {
                this.albums = response.data.response;
                this.getGenres();
            })
            .catch((err) => {
                console.log(`error ${err}`);
            });
        },
        getGenres() {
            for(let i = 0; i < this.albums.length; i++) {
                if(!this.genres.includes(this.albums[i].genre))
                this.genres.push(this.albums[i].genre);
            }
        },
        selectGenre(genre) {
            this.selectedGenre = genre;
        }
    }
}
</script>

<style lang="scss" scoped>
    .container {
        display: flex;
        flex-wrap: wrap;
        justify-content: space-evenly;
    }
</style>
