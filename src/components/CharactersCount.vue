<template>

    <div class="alert alert-success" role="alert">
        {{numeroPassato}} risultati di ricerca
    </div>

</template>

<script>
export default {
    name: 'CharactersCount',
    props: {
        numeroPassato: Number
    }
}
</script>

<style>

</style>