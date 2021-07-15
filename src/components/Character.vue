<template>
    <div class="character-container">
        <div class="inner">
            <img :src="image" :alt="`image of ${name}`" />
            <div class="name" v-html="nameHtml"/>
            <div class="line"/>
            <div class="origin">{{origin}}</div>
            <div class="species">{{species}}</div>
        </div>
    </div>    
</template>


<script>
export default {
    name: 'Character',
    props: {
        name: String,
        origin: String,
        species: String,
        image: String,
        inputSearch: String
    },
    computed: {
        nameHtml() {
            // piccolo hack per evidenziare la parte ricercata dall'utente all'interno del name.

            const search = this.inputSearch.toLowerCase()

            if(this.name.toLowerCase().includes(search)) {
                return this.name.replace(search, `<span style="background:yellow">${search}</span>`)
            }

            return this.name
        }
    }
}
</script>

<style lang="scss" scoped>

.character-container {
    text-align: center;

    .inner {
        padding: 15px;

        img {
            border-radius: 50%;
            width:100%;
            box-shadow: 1px 1px 6px #aaa;
        }

        .name {
            font-size: 24px;

        }

        .line {
            width: 30%;
            height: 4px;
            margin: 15px auto;
            background: #000;
        }

        .species {
            font-weight: bold;
        }

    }

}

</style>