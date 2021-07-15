<template>
    <h1>
        Rick and Morty App
        <!--
            Inseriamo in Header un campo di ricerca.
            
            Quando l'utente digita nel campo di ricerca, 
            Header.vue lancerà un evento verso il padre

            App.vue in ascolto di questo evento dall'Header.vue,
            agirà di conseguenza.

            =>  All'ascolto di un evento dall'Header, App.vue
            lancia un metodo.

            è molto simile al: 
            "Quando il button lancia il click, App.vue lancia un suo method".

        -->

        <input type="text" placeholder="Search" v-model="searchString" />
        <button @click="$emit('search', searchString)">Search</button>
        <!--

            quando l'utente clicca sul button, il button fa l'"emit" verso
            il padre (App.vue) di "search" con il dato searchString.

         -->

    </h1>    
</template>


<script>
export default {
    name: 'Header',
    data() {
        return {
            searchString: ''
        }
    }
}
</script>

<style lang="scss" scoped>
    h1 {
        font-size: 40px;
        text-align: center;
        padding: 50px 0;
    }
</style>

