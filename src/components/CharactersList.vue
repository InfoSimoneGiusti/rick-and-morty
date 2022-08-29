<template>

    <div class="container">
        <LoadInProgress v-if="loadInProgress" />

        <MySearch @effettuaRicerca="setSearchText" />

        <CharactersCount :numeroPassato="getFilteredCharacters.length"/>

        <div class="row row-cols-4 g-3">
            <SingleCharacter  v-for="character in getFilteredCharacters" :key="character.id" :character="character" />
        </div>

    </div>

</template>

<script>

import axios from 'axios';
import SingleCharacter from './SingleCharacter.vue';
import LoadInProgress from './LoadInProgress.vue';
import MySearch from './MySearch.vue';
import CharactersCount from './CharactersCount.vue';

export default {
    name: 'CharactersList',
    components: {
        SingleCharacter,
        LoadInProgress,
        MySearch,
        CharactersCount
    },
    data() {
        return {
            charactersList: [],
            endpoint: 'https://api.sampleapis.com/rickandmorty/characters',
            loadInProgress: true,
            searchText: ''
        }
    },
    computed: {
        getFilteredCharacters() {
            
            if (this.searchText == '') {
                return this.charactersList;
            } else {
               
               const valoriFiltrati = this.charactersList.filter((character => {
                    if (character.name.toLowerCase().includes(this.searchText.toLowerCase())) {
                        return true;
                    } else {
                        return false;
                    }
               }));  

               return valoriFiltrati;

            }
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
        },
        setSearchText (text) {
            this.searchText = text;
        }
    }
}
</script>

<style>

</style>