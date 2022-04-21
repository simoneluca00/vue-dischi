<template>
    <div class="container">
        <div class="playlist">

            <LoaderComp v-if="loading" />

            <CardSong v-for="(element, index) in filteredGenre" :key="index" :poster="element.poster" :title="element.title"
                :author="element.author" :year="element.year" v-else />
        </div>
        <div class="selectFilter">
            <SelectGenre @selectGenre="chooseGenre" v-if="!loading"/>
        </div>
    </div>
</template>

<script>
    import axios from 'axios';
    import CardSong from './partials/CardSong.vue';
    import LoaderComp from './partials/LoaderComp.vue'
    import SelectGenre from './partials/SelectGenre.vue'


    export default {
        name: 'PlaylistComp',

        components: {
            CardSong,
            LoaderComp,
            SelectGenre,

        },

        data() {
            return {
                // modificare il nome dell'array
                music: [],
                loading: false,
                selectedGenre: "",
            }
        },

        created() {

            this.loading = true;

            // modificare il link con l'api che si vuole usare
            axios.get('https://flynn.boolean.careers/exercises/api/array/music')

                .then((res) => {

                    this.music = res.data.response
                })

                .catch((error) => {
                    console.log(error)
                })

                .finally(() => (this.loading = false))

        },

        computed: {
            filteredGenre() {
                if (this.selectedGenre == "") {
                    return this.music
                }

                return this.music.filter((element) => {
                    return element.genre
                        .toLowerCase()
                        .includes(this.selectedGenre.toLowerCase())
                })
            }
        },

        methods: {
            chooseGenre(genre) {
                this.selectedGenre = genre
            }
        }

    }
</script>


<style scoped lang="scss">
    .container {
        height: 100%;
        width: 100%;
        display: flex;
        
        .playlist {
            width: 75%;
            height: 100%;
            overflow-y: auto;
            display: flex;
            justify-content: flex-start;
            align-items: flex-start;
            flex-wrap: wrap;
        }

        .selectFilter {
            width: 25%;
            display: flex;
            height: 100%;
            justify-content: center;
            align-items: center;
        }
    }

</style>