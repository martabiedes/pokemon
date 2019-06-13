<template>
  <div class="col-3">
    <div class="card" style="width: 18rem;">
        <img class="card-img-top" v-bind:src="pokemon.sprites.front_shiny" v-bind:alt="pokemon.name">
        <div class="card-body">
            <h5 class="card-title text-captialize">{{pokemon.name}}</h5>
            <p class="card-text">Height={{pokemon.height}}</p>
            <p class="card-text">Weight={{pokemon.weight}}</p>
        </div>
    </div>  
  </div>
</template>

<script>
export default {
  name: 'card',
  data: function(){
      return {
          pokemon: null
      }
  },
  props: {
    url: String
  },
  mounted: function(){
      console.log("mounted fucntion ran")

      const axios = require('axios');
      const vm = this;

      axios({
    method: 'get',
    url: vm.url,
    responseType: 'stream'
    })
  .then(function (response) {
    console.log(response.data);
    vm.pokemon = response.data
  });
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.card{
    text-align: center;
    margin-bottom: 30px;
}
</style>
