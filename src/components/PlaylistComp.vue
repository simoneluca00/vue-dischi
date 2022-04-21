<template>
    <div class="container">
        <div class="playlist">

            <h2 class="noResults" v-if="filterList.length == 0">Prova a cercare qualcos'altro...</h2>

            <LoaderComp v-if="loading" />

            <!-- come combinare i due array filtrati (genere e artista?) -->
            <CardSong v-for="(element, index) in filterList" :key="index" :poster="element.poster"
                :title="element.title" :author="element.author" :year="element.year" v-else />
        </div>
        <div class="selectFilter">
            <SelectGenre @selectGenre="chooseGenre" v-if="!loading" />
            <SelectArtist @selectArtist="chooseArtist" v-if="!loading" />
        </div>
    </div>
</template>

<script>
    import axios from 'axios';
    import CardSong from './partials/CardSong.vue';
    import LoaderComp from './partials/LoaderComp.vue'
    import SelectGenre from './partials/SelectGenre.vue'
    import SelectArtist from './partials/SelectArtist.vue'


    export default {
        name: 'PlaylistComp',

        components: {
            CardSong,
            LoaderComp,
            SelectGenre,
            SelectArtist

        },

        data() {
            return {
                // modificare il nome dell'array
                music: [],
                loading: false,
                selectedGenre: "",
                selectedArtist: "",
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
            filterList() {
                if (this.selectedGenre == "" && this.selectedArtist == "") {
                    return this.music
                }

                return this.music
                    .filter((element) => {
                        return element.genre
                            .toLowerCase()
                            .includes(this.selectedGenre.toLowerCase())


                    })
                    .filter((element) => {
                        return element.author
                            .toLowerCase()
                            .includes(this.selectedArtist.toLowerCase())
                    })
            },

        },

        methods: {
            chooseGenre(genre) {
                this.selectedGenre = genre
            },

            chooseArtist(text) {
                this.selectedArtist = text
            }
        }

    }
</script>


<style scoped lang="scss">
    .container {
        height: 100%;
        width: 100%;
        display: flex;
        justify-content: center;

        .playlist {
            width: 80%;
            height: 100%;
            overflow-y: auto;
            display: flex;
            justify-content: center;
            align-items: flex-start;
            flex-wrap: wrap;

            .noResults {
                color: #fff;
                align-self: center;
            }
        }

        .selectFilter {
            width: 20%;
            height: 100%;
            display: flex;
            flex-direction: column;
            justify-content: space-around;
            align-items: center;
            border-left: 1px solid #2e3a46
        }
    }
</style>