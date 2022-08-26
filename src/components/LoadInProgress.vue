<template>
  <div class='loading'>
    <h2>Caricamento in corso...</h2>
  </div>
</template>

<script>
export default {
    name: 'LoadInProgress'
}
</script>

<style lang="scss">

    @import '@/styles/vars.scss';

    .loading {
        position: fixed;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        display: flex;
        justify-content: center;
        align-items: center;
        background-color: #fff;

        h2 {
            font-size: 5rem;
            color: $text_color;
        }
    }
</style>