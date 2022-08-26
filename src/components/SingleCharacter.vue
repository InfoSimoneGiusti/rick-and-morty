<template>
  <div class="col">
    <div class="card text-center">
      <img :src="character.image" class="card-img-top"/>

      <div class="card-body">
        <h3 class="card-title ms_separator">{{character.name}}</h3>
        <p class="card-text mt-4">{{character.origin}}</p>
        <p class="card-text fw-bold">{{character.species}}</p>
      </div>

    </div>
  </div>
</template>

<script>
export default {
    name: 'SingleCharacter',
    props: {
        character: Object
    }
}
</script>

<style lang="scss">

  .ms_separator {

    position: relative;

    &::after {
      content: "";
      display: block;
      border-bottom: solid 1px #000;
      width: 20%;
      left: 40%;
      margin-top: 10px;
      position: absolute;

    }
  }
    

</style>