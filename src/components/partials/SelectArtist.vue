<template>
    <div>
        <label for="optArtist">Filtra in base agli artisti:</label>
        <select name="optArtist" id="optArtist" v-model="artist" @change="$emit( 'selectArtist', artist )">
            <option value="">Scegli l'artista</option>
            <option value="Bon Jovi">Bon Jovi</option>
            <option value="Queen">Queen</option>
            <option value="Sting">Sting</option>
            <option value="Steve Gadd Band">Steve Gadd Band</option>
            <option value="Iron Maiden">Iron Maiden</option>
            <option value="Eric Clapton">Eric Clapton</option>
            <option value="Deep Purple">Deep Purple</option>
            <option value="Metallica">Metallica</option>
            <option value="Dave Weckl">Dave Weckl</option>
            <option value="Michael Jacjson">Michael Jacjson</option>
        </select>
    </div>
</template>

<script>
    export default {
        name: 'SelectArtist',

        data() {
            return {
                artist: "",
            }
        },

    }
</script>


<style scoped lang="scss">
    label {
        color: #fff;
        display: block;
        margin: 50px 0 10px 0;
    }

    select {
        padding: 5px 16px 5px 5px;
    }
</style>