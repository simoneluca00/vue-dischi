<template>
    <div class="card">
        <img :src="poster" :alt="'copertina ' + title">
        <h3>{{title}}</h3>
        <span>{{author}}</span>
        <span>{{year}}</span>
    </div>
</template>

<script>
    export default {
        name: 'CardSong',
        props: {
            poster: String,
            title: String,
            author: String,
            year: String,
        }

    }
</script>


<style scoped lang="scss">
    .card {
        flex-basis: calc((100% / 5) - 40px);
        margin: 20px;
        padding: 20px;
        background-color: #2e3a46;
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
        text-align: center;

        img {
            width: 130px;
            height: 130px;
        }

        h3 {
            color: white;
            text-transform: uppercase;
            margin: 25px 0 15px 0;
        }

        span {
            color: #7a7b75;
            margin: 5px 0;
        }
    }
</style>