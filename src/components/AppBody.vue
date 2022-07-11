<template>

    <main>
        <BodyComponent />
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

</style>
