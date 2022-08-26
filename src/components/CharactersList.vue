<template>

    <div class="container">
        <LoadInProgress v-if="loadInProgress" />

        <div v-else class="row row-cols-4 g-3">
            <SingleCharacter  v-for="character in charactersList" :key="character.id" :character="character" />
        </div>



    </div>

</template>

<script>

import axios from 'axios';
import SingleCharacter from './SingleCharacter.vue';
import LoadInProgress from './LoadInProgress.vue';

export default {
    name: 'CharactersList',
    components: {
        SingleCharacter,
        LoadInProgress
    },
    data() {
        return {
            charactersList: [],
            endpoint: 'https://api.sampleapis.com/rickandmorty/characters',
            loadInProgress: true
        }
    },
    created() {
        this.getCharacters();
    },
    methods: {
        getCharacters() {
            let that = this;
            axios.get(this.endpoint)
            .then(function (response) {
                that.charactersList = response.data;
                that.loadInProgress = false;
            })
            .catch(err => {
                console.log(err);
                that.loadInProgress = false;
            });
        }
    }
}
</script>

<style>

</style>