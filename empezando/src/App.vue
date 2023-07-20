<script setup>
import {ref,computed} from "vue";

 
  const arrayProduct = [
      {
        nombre: "ervigio",
        precio: 110,
        finDeSemana: true
      },
      {
        nombre: "ATANAGILDO",
        precio: 125,
        finDeSemana: false
      },
      {
        nombre: "LEOVIGILDO",      
        precio: 73,
        finDeSemana: true
      },
      {
        nombre: "ATAULFO",
        precio: 69,
        finDeSemana: true
      },
      {
        nombre: "SISEBUTO",
        precio: 105,
        finDeSemana: false
      },
      {
        nombre: "TEODORICO",
        precio: 112,
        finDeSemana: true
      },
      {
        nombre: "RECESVINTO",
        precio: 71,
        finDeSemana: false
      }
    ];

    const contador = ref(0);
    const total = 7;
    const ruta = "https://www.html6.es/img/rey_";
    const siguiente=() =>{
        contador.value++;
        if(contador.value>=total){
          contador.value=0;
        };
      };

    const rey = computed(() => {
      const elNombre= arrayProduct[contador.value].nombre.toLowerCase()
      return elNombre.substring(0,1).toUpperCase() + elNombre.substring(1)
    });

    const imagen=computed(() => {
      return `${ruta}${arrayProduct[contador.value].nombre.toLowerCase()}.png`
    });

    const nuevoPrecio = computed(() =>{
      return Number(arrayProduct[contador.value].precio/1.10).toFixed(2);
    })

</script>

<template>

  <h2>Cena {{contador+1}}
  con el rey godo {{ rey }}
  </h2>
  <h3 class="precio">Precio: {{ arrayProduct[contador].precio }}€</h3>
  <div v-if="arrayProduct[contador].finDeSemana" class="soloFinesDeSemana dias">(Solos fines de semana)</div>
  <div v-else class="dias todosLosDias">(De lunes a domingo)</div>
  <div v-if="arrayProduct[contador].precio<100" class="oferta">
    <div>Ahora un 10% dto: {{ nuevoPrecio}}€</div>
    <img src="/ofertax.jpeg" alt="rey godo en descuento" />
  </div>
  <img :src="imagen" alt="">
  <button @:click="siguiente">Siguiente ({{contador + 1}}/ {{total}})</button>





</template>

<style scoped>

.todosLosDias{
  background-color: green;
}

.soloFinesDeSemana{
  background-color: red;
}

.dias{
  color:white;
  padding: 4px 17px;
  font-size:0.9em;
  border-radius:4px;
  margin: 5px 0 10px;
  display:inline-block;
}

.oferta img{
  width:65px;
  margin:12px 5px
}
</style>
