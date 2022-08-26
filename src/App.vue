<template>
  <div id="app">

    <MyHeader message="Rick and Morty App" />
    <CharactersList />
    
  </div>
</template>

<script>
import MyHeader from './components/MyHeader.vue';
import CharactersList from './components/CharactersList.vue'

export default {
  name: 'App',
  components: {
    MyHeader,
    CharactersList
  }
}
</script>

<style lang="scss">
  @import '@/styles/general.scss';

</style>
