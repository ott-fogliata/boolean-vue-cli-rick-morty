<template>
    <div class="row">
        <Character class="col-6 col-md-3" v-for="character in characters" 
        :key='character.id' 
        :name='character.name'
        :origin='character.origin'
        :species='character.species'
        :image='character.image'
        />    
    </div>    
</template>


<script>

import Character from './Character.vue'

export default {
    name: 'Main',
    components: {
        Character
    },
    props: {
        characters: Array
    }
}
</script>

<style lang="scss" scoped>
 
</style>