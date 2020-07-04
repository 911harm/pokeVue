<template>
  <div class="Pokemones">
    <h1>Pokemones</h1>
    <input type="search" placeholder="Busca tu pokemon" v-model="search">
    <div class="container">
      <ul>
      <li  v-for="(pokemon,$index) in pokedex" :key="$index">
       <div class="pokemon-container">
        <div class="container-bk">
          <a style="background-color:transparent;" :href="`https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/${pokemon.entry_number}.png`">
            <img :src="`https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/${pokemon.entry_number}.png`" alt="ya viene">
          </a>
          <div class="poke-inf" >
            <h5 >{{pokemon.pokemon_species.name | capitalize}}</h5>
          </div>
         </div>  
       </div>
      </li>
    </ul>
    </div>
  </div>
</template>
<script>
export default {
  name:"Pokemones",
  data(){
    return{
        pokemones:[],
        search:""

    }
  },
  created(){
    //fetch("https://pokeapi.co/api/v2/pokemon/?offset=0&limit=100")
    fetch("https://pokeapi.co/api/v2/pokedex/1/")
   .then(res=>res.json())
    .then(res=>res.pokemon_entries)
    .then(res=>this.pokemones=res)
    //.then(res=>console.log(res))
  },
  filters:
  {
  capitalize: function (value) {
    if (!value) return ''
    value = value.toString()
    return value.charAt(0).toUpperCase() + value.slice(1)
  }
 },
 computed:{
  pokedex(){
   if (!this.search) {
        return this.pokemones
      }

      return this.pokemones
        .filter(a => a.pokemon_species.name.toLowerCase().includes(this.search.toLowerCase()))

    
    },
  
  
  }
}

</script>
<style scoped>
*{
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
.pokemon-container{
  float:left;
  border:2px solid rgba(0, 255, 234,0.7);
  width: 30%;
  height: 175px;
   margin: 10px 10px;
   padding: 5px 10px;
   border-radius: 50px 20px;
   box-shadow: 10px 10px 5px grey;
}
ul{
  list-style-type: none;
}
.Pokemones{
  width: 80%;
  margin: 0 auto;
  align-items: center;
  
}
img{
  width: 130px;
}
.container-bk
{
  background-color: #eee;
  height: auto;
  border-radius: 50px 20px;
}
.poke-inf{
width: 100%;
height: 25px;
position:relative;
background-image: url("../img/trapecio.png");
background-repeat: no-repeat;
background-size: cover;
background-position: center top;
text-align: center;
padding-top: 1px;
}


</style>