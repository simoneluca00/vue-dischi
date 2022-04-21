<template>
    <div>
        <select name="musicalGenre" id="musicalGenre" v-model="chooseOption" @change="$emit( 'selectGenre', chooseOption )">
            <option value="" disabled>Scegli il genere</option>
            <option value="Pop">Pop</option>
            <option value="Rock">Rock</option>
            <option value="Metal">Metal</option>
            <option value="Jazz">Jazz</option>
        </select>
    </div>
</template>

<script>

  export default {
    name: 'SelectGenre',

    data() {
        return {
            chooseOption : "",
        }
    },

  }

</script>


<style scoped lang="scss">
    select {
        padding: 5px 30px 5px 5px;
    }
</style>