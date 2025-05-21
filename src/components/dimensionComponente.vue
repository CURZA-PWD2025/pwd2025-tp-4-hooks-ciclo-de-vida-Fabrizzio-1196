<template>
    <div>
      <h2>Dimensiones del componente</h2>
      <p>Ancho: {{ ancho }}px</p>
      <p>Alto: {{ alto }}px</p>
    </div>
  </template>
  
  <script setup>
  import { ref, onMounted, onUnmounted } from 'vue';
  
  const ancho = ref(window.innerWidth);
  const alto = ref(window.innerHeight);
  
  function actualizarDimensiones() {
    ancho.value = window.innerWidth;
    alto.value = window.innerHeight;
  }
  
  onMounted(() => {
    window.addEventListener('resize', actualizarDimensiones);
  });
  
  onUnmounted(() => {
    window.removeEventListener('resize', actualizarDimensiones);
  });
  </script>
  
  <style scoped>
  h2 {
    margin-bottom: 8px;
  }
  </style>