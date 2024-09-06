<template>
<div class="container contenido">
<div class="row">

<div class="col-6 form">
<form @submit.prevent="agregarPersona">
  <div class="mb-3">
    <label for="exampleInputEmail1" class="form-label">Nombre</label>
    <input type="text" class="form-control" id="nombre" v-model="nombre">
  </div>
  <div class="mb-3">
    <label for="exampleInputPassword1" class="form-label">Edad</label>
    <input type="number" class="form-control" id="edad" v-model="edad">
  </div>
  <button type="submit" class="btn btn-primary">Agregar</button>
</form>
</div>

<div class="col-6 tabla">
<table class="table table-striped">
  <thead>
    <tr>
      <th scope="col">#</th>
      <th scope="col">Nombre</th>
      <th scope="col">Edad</th>
    </tr>
  </thead>
  <tbody>
    <tr v-for="(persona, index) in personas" :key="index">
       <th scope="row">{{ index + 1 }}</th>
       <td>{{ persona.nombre }}</td>
       <td>{{ persona.edad }}</td>
    </tr>
  </tbody>
</table>
            </div>
        </div>
    </div>
</template>

<script setup>

import { ref } from 'vue';

const nombre = ref('');
const edad = ref('');
const personas = ref([]);

const agregarPersona = () => {
  if (nombre.value && edad.value) {
    personas.value.push({ nombre: nombre.value, edad: edad.value });
    nombre.value = '';
    edad.value = '';
  } else {
    alert('Por favor, complete todos los campos.');
  }
};



</script>

<style scoped>
 .contenido{
    width: 100%;
    height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
    color: white;

 }

 .row{
    width: 100%;
    gap: 30px;
 }

 .form{
    width: 40%;
 }

</style>