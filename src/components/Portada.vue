<template>
    <div class="portada">
        <h1>
            {{Mensage}}
        </h1>
    </div>
</template>
<script>
export default {
    name:"Portada",
    data(){
        return{
            Mensage:"Bienvenidos a la Clase de Pokemones"

        }
    }
}
</script>
<style scoped>
h1{
    font-family:Verdana, Geneva, Tahoma, sans-serif;
    color:#444;

}

</style>