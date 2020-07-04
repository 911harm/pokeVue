<template>
  <div class="home">
    <img alt="Picachi" :src='imagenP'>
    <Portada/>

  </div>
</template>

<script>
// @ is an alias to /src

import Portada from "@/components/Portada"


export default {
  name: 'Home',
  data(){
    return {
      imagenP:""
      
    }
  },
  components:{
    Portada
  },
  created(){
    {
      fetch("https://pokeapi.co/api/v2/pokemon/25")
      .then(res=>res.json())
      .then(res=> res.sprites.front_default)
      .then(res=>this.imagenP=res)


    }
  }
 
}
</script>
<style scoped>
img{
  width: 300px;
  height: auto;
  
}
</style>>

