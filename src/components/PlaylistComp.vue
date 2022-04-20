<template>
    <div class="container">

        <LoaderComp v-if="loading" />

        <CardSong v-for="(element, index) in music" :key="index" :poster="element.poster" :title="element.title"
            :author="element.author" :year="element.year" v-else />

    </div>
</template>

<script>
    import axios from 'axios';
    import CardSong from './partials/CardSong.vue';
    import LoaderComp from './partials/LoaderComp.vue'


    export default {
        name: 'PlaylistComp',

        components: {
            CardSong,
            LoaderComp,
        },

        data() {
            return {
                // modificare il nome dell'array
                music: [],
                loading: false,
            }
        },

        created() {

            this.loading = true;

            // modificare il link con l'api che si vuole usare
            axios.get('https://flynn.boolean.careers/exercises/api/array/music')

                .then((res) => {

                    this.music = res.data.response
                    console.log(this.music)
                })

                .catch((error) => {
                    console.log(error)
                })

                .finally(() => (this.loading = false))

        },

        methods: {

        }

    }
</script>


<style scoped lang="scss">
    .container {
        width: 75%;
        height: 100%;
        overflow-y: auto;
        display: flex;
        justify-content: center;
        flex-wrap: wrap;
    }
</style>