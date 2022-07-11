<template>
    <div class="single-album">
        <img :src="img" :alt="name">

        <div class="album-title">{{ name.toUpperCase() }}</div>
        <div class="album-author">{{ author }}</div>
        <div class="album-year">{{ year }}</div>
    </div>
</template>

<script>
export default {
    name: "BodyComponent",
    props: {
        img: String,
        name: String,
        author: String,
        year: String
    },
    data() {
        return {

        }
    },
}
</script>

<style lang="scss" scoped>
    .single-album {
        background-color: #2e3a46;
        margin: 1rem;
        width: 15rem;
        padding: 1rem;
        display: flex;
        flex-direction: column;
        align-items: center;

        div {
            text-align: center;
        }
        .album-title {
            margin: 1rem 0;
            color: white;
            font-weight: 800;
        }

        .album-author, .album-year {
            color: #7f7a74;
        }
    }
</style>