<template>
    <div>
      <h2>Lista de profesiones</h2>
      <ul v-if="cargando === false">
        <li v-for="(item, index) in lista" :key="index">
          {{ item }}
        </li>
      </ul>
      <p v-else>Cargando lista...</p>
    </div>
  </template>
  
  <script setup>
  import { ref, onMounted } from 'vue';
  import { profesiones } from '../resource/profesiones'; 
  
  const lista = ref([]);
  const cargando = ref(true);
  
  onMounted(() => {
    setTimeout(() => {
      lista.value = profesiones;
      cargando.value = false;
    }, 3000); 
  });
  </script>
  
  <style scoped>
  h2 {
    margin-bottom: 10px;
  }
  </style>