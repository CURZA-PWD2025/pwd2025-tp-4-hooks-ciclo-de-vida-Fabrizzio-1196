<template>
  <div>
    <h1>Componentes</h1>

    <div class="botones">
      <button @click="componenteActual = 'Lista'">Lista</button>
      <button @click="componenteActual = 'Tareas'">Tareas</button>
      <button @click="componenteActual = 'DimensionComponente'">Dimensiones</button>
    </div>

    <component :is="componentes[componenteActual]" />
  </div>
</template>

<script setup>
import { ref } from 'vue';

import Lista from './components/lista.vue';
import Tareas from './components/tareas.vue';
import DimensionComponente from './components/dimensionComponente.vue';

const componenteActual = ref('Lista');

const componentes = {
  Lista,
  Tareas,
  DimensionComponente
};
</script>

<style scoped>
.botones {
  margin-bottom: 20px;
}
button {
  margin-right: 10px;
  padding: 8px 12px;
  cursor: pointer;
}
</style>