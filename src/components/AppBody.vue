<template>

    <main>
        <SearchBar :genres="genres" :artists="artists" @genreSelection="selectGenre" @artistSelection="selectArtist" />

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
            artists: ["All"],
            selectedGenre: "All",
            selectedArtist: "All"
        }
    },
    computed: {
        filteredAlbums() {
            let albums = [];
            if(this.selectedGenre === "All" && this.selectedArtist === "All") {
                albums = this.albums
            } else {
                this.albums.forEach((album) => {
                    if(album.genre === this.selectedGenre && this.selectedArtist === "All" ) {
                    albums.push(album);
                } else if(album.genre === this.selectedGenre && album.author === this.selectedArtist) {
                    albums.push(album) 
                } else if(this.selectedGenre === "All" && album.author === this.selectedArtist) {
                    albums.push(album)
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
                this.getArtists();
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
        getArtists() {
            for(let i = 0; i < this.albums.length; i++) {
                if(!this.artists.includes(this.albums[i].author))
                this.artists.push(this.albums[i].author);
            }
        },
        selectGenre(genre) {
            this.selectedGenre = genre;
        },
        selectArtist(artist) {
            this.selectedArtist = artist;
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
