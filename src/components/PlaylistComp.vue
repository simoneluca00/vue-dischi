<template>
    <div class="container">
        <CardSong 
            v-for="(element, index) in music"
            :key="index"
            :poster="element.poster"
            :title="element.title"
            :author="element.author"
            :year="element.year"


        />
    </div>
</template>

<script>

import axios from 'axios';
import CardSong from './partials/CardSong.vue';


export default {
  name: 'PlaylistComp',

    components: {
      CardSong,
  },

    data(){
        return {
        // modificare il nome dell'array
        music: [],
    }
    },

    created(){
        // modificare il link con l'api che si vuole usare
    axios.get('https://flynn.boolean.careers/exercises/api/array/music')
    .then((res) => {

        // console.log(res)
        this.music = res.data.response
        console.log(this.music)
    })
    //   scrittura predefinita per avere in console tutti gli errori (CATCH)
    .catch((error)=>{console.log(error)})
    }
  
}
</script>


<style scoped lang="scss">

    .container {
        width: 75%;
        height: 90%;
        display: flex;
        justify-content: space-between;
        flex-wrap: wrap;
    }

</style>