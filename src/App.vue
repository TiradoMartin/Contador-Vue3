
<template>
  <div class="container">
    <h1 v-show="!visible"> Hola {{ miNombre }}</h1>
    <input v-show="!visible" @change="chageValue" class="input" type="text">
    <div v-show="visible" class="contador">
  <h1>Hola {{ miNombre }}</h1>
  <button @click="decrement">-</button>
  <span :class="miColor">{{ contador }}</span>
   <button  @click="increment">+</button>
   <div v-if="contador<0">El contador no puede ser menor a 0</div>
   <div v-else-if="contador>=20">El contador no puede ser mayor a 20</div>

   <div v-show="comprobar">El contador no puede ser 0</div>
  </div>
  </div>
</template>
<script setup >
import { ref,computed } from 'vue'
let miNombre = ref('Ingresa tu nombre')
let contador = ref(0)
let miColor = ref('color')
let visible = ref(false)
const increment = () => {contador.value++;
  colorSelet();
}
const decrement = () => {contador.value--
  colorSelet();
}
const colorSelet=()=>{
  if(contador.value < 0){
    miColor.value = 'red'
}else if (contador.value > 10){
    miColor.value = 'green'
}else{
    miColor.value = 'color'
}}

const comprobar =computed(()=>{
  return contador.value ===0
})
const chageValue = (e) => {
  miNombre.value = e.target.value
  visible.value = true
}
</script>

<style scoped>
.color{color:blue;}
.red{color:red;}
.green{color:green;}  
span{margin:5px 10px;}
button{
  margin:5px 10px;
  padding:5px 10px;
  border-radius:5px;
  width: 20%;
  height: 10%;
  border:1px solid black;
  background-color:lightblue;

}

span{
  font-size: 30px;
  font-weight: bold;
}
.container{
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
}
.contador{
  border:1px solid black;
  padding: 5em;
  border-radius: 10px;
}
.input{
  margin:5px 10em;
  padding:5px 5px;
  border-radius:5px;
  width: 15%;
  height: 5%;
  border:1px solid black;
  background-color:lightblue;
}
</style>