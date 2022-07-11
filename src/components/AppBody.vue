<template>

    <main>
        <div class="container">
            <BodyComponent v-for="album, index in albums" :key="index"
            :img="album.poster"
            :name="album.title"
            :author="album.author"
            :year="album.year"
            />
        </div>
    </main>

</template>

<script>
import axios from 'axios';  
import BodyComponent from './BodyComponent.vue'

export default {
    name: "AppBody",
    components: {
        BodyComponent,
    },
    data() {
        return {
            url: "https://flynn.boolean.careers/exercises/api/array/music",
            albums: []
        }
    },
    computed: {

    },
    created() {
        this.getAlbums();
    },
    methods: {
        getAlbums() {
            axios.get(this.url).then((response) => {
                this.albums = response.data.response;
            })
            .catch((err) => {
                console.log(`error ${err}`);
            });
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
