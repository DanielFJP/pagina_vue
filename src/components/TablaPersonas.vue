<template>
<div class="container">
<div class="row contenido">
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
      <th scope="col">Agregar</th>
    </tr>
  </thead>
  <tbody>
    <tr v-for="(persona, index) in personas" :key="index">
       <th scope="row">{{ index + 1 }}</th>
       <td>{{ persona.nombre }}</td>
       <td>{{ persona.edad }}</td>
       <td>
        <button @click="adicionarPersona(persona)" class="btn btn-success">Adicionar</button>
       </td>
    </tr>
  </tbody>
</table>
</div>
</div>

<div class="row">
    <div class="col-12">
        <h3>Personas Seleccionadas:</h3>
        <ul>
            <li v-for="(persona, index) in personasSeleccionadas" :key="index">
                {{ persona.nombre }} - {{ persona.edad }} años.
            </li>
        </ul>
    </div>
</div>
    </div>
</template>

<script setup>

import { ref } from 'vue';

const nombre = ref('');
const edad = ref('');
const personas = ref([]);
const personasSeleccionadas = ref([]);

const agregarPersona = () => {
  if (nombre.value && edad.value) {
    personas.value.push({ nombre: nombre.value, edad: edad.value });
    nombre.value = '';
    edad.value = '';
  } else {
    alert('Por favor, complete todos los campos.');
  }
};

const adicionarPersona = (persona) => {
    if (!personasSeleccionadas.value.includes(persona)) {
        personasSeleccionadas.value.push(persona);
    } else {
        alert('la persona ya esta en la lista.')
    }
};

</script>

<style scoped>
 .contenido{
    width: 100%;
    height: auto;
    display: flex;
    justify-content: center;
    align-items: center;
    color: white;
    gap: 30px;
    margin-bottom: 50px;
    margin-top: 50px;
 }


 .form{
    width: 40%;
 }

 h3{
   color: white;
 }

 ul{
    padding-left: 0;
    list-style-type: none;
 }

 li{
    background-color: white;
    padding: 10px;
    margin-bottom: 5px;
    border-radius: 5px;
    color: black;
    font-weight: 800;
 }

 

</style>