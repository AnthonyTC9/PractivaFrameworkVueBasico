<script setup>

  /*const miNombre = "Antonio";
  const miEdad=18;
  const miColor = "color:green; font-size:3em";
  const selector="azul"
  const saludar = () =>{
    console.log("hola");
  };
    const saludar2 = (nombre) =>{
    console.log(`hola ${nombre}`);
  };*/
  import {ref,computed} from "vue";
  import {productos} from "./datos.js";



  const contador=ref(0);
  const miColor = ref("azul");

  const decremento = () =>{
    contador.value--;
    if(contador.value<0){
      miColor.value="rojo";
    }
  };

    const incremento = () =>{
    contador.value++;
        if(contador.value>5){
      miColor.value="verde";
    }
  };

  const comprobacion = computed(()=>{
    
    return contador.value===0;  


  });
  
</script>

<template>

  <img :src="imagen1">

  <button @click="decremento">-</button>
  <span :class="miColor"> {{contador}} </span>
  <button @click="incremento">+</button>
  <div v-if="contador<0">Escribe una cantidad mayor de 0</div>
  <div v-else-if="contador >=5">Escribe una cantidada menor de 5</div>
  <div v-show="comprobacion">No esta permitido el numero 0</div>

<!--
  <h1 v-bind:class="selector" >
    Hola {{miNombre}} y tendre {{miEdad+1}}
  </h1>
    <h2 v-bind:style="miColor" >
    Hola {{miNombre}} y tendre {{miEdad+1}}
  </h2>
  <button v-on:click="saludar">Aceptar</button>
  <button @click="saludar2(miNombre)">Aceptar</button>
  -->

</template>

<style scoped>
  span{
    padding:0 5px;
  }
  .rojo{
    color: red;
  }
  .verde{
    color:green;
  }
  .azul{
    color:blue;
  }
</style>
