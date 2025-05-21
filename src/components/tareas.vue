<template>
    <div>
      <h2>Lista de Tareas</h2>
      <input v-model="nuevaTarea" @keyup.enter="agregarTarea" placeholder="Agregar tarea" />
      <button @click="agregarTarea">Agregar</button>
      
      <ul>
        <li
          v-for="(tarea, index) in tareas"
          :key="index"
          :class="{ antigua: index < tareasPrevias.length }"
        >
          {{ tarea }}
        </li>
      </ul>
    </div>
  </template>
  
  <script setup>
  import { ref, onBeforeUpdate, onUpdated } from 'vue';
  
  const tareas = ref(['Aprender Vue']);
  const tareasPrevias = ref([...tareas.value]);
  const nuevaTarea = ref('');
  
  function agregarTarea() {
    if (nuevaTarea.value.trim() !== '') {
      tareas.value.push(nuevaTarea.value.trim());
      nuevaTarea.value = '';
    }
  }
  
  onBeforeUpdate(() => {
    console.log('Lista aún no modificada');
    tareasPrevias.value = [...tareas.value];
  });
  
  onUpdated(() => {
    console.log('Lista modificada');
  });
  </script>
  
  <style scoped>
  .antigua {
    color: teal;
    font-weight: bold;
  }
  input {
    margin-right: 8px;
  }
  </style>