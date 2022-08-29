<template>
    <form>
        <div class="mb-3 d-flex">
            <input placeholder="Personaggio da ricercare" type="text" class="form-control" id="search" v-model="searchText">
            <button @click.prevent="$emit('effettuaRicerca', searchText)" class="btn btn-primary ms-3">Cerca</button>
            <button @click.prevent="reset" class="btn btn-warning ms-3">Reset</button>
        </div>
    </form>
</template>

<script>
export default {
    name: 'MySearch',
    data() {
        return {
            searchText: ''
        }
    },
    methods: {
        reset() {
            this.searchText = '';
            this.$emit('effettuaRicerca', this.searchText);
        }
    }
}
</script>

<style>

</style>