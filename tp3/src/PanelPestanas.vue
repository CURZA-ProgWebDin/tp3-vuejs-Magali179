<template>

  <div>

    <h1>Panel de pestañas</h1>

    <div class="botones">

      <button
        @click="tabActiva = 'todos'"
      >
        Todos
      </button>

      <button
        @click="tabActiva = 'electronica'"
      >
        Electrónica
      </button>

      <button
        @click="tabActiva = 'perifericos'"
      >
        Periféricos
      </button>

    </div>

    <KeepAlive>

      <component
        :is="componenteActual"
      />

    </KeepAlive>

  </div>

</template>

<script setup>

import {
  ref,
  computed
} from 'vue'

import TabTodos
from './components/tabs/TabTodos.vue'

import TabElectronica
from './components/tabs/TabElectronica.vue'

import TabPerifericos
from './components/tabs/TabPerifericos.vue'

const tabActiva = ref('todos')

const componenteActual = computed(() => {

  if (tabActiva.value === 'todos') {

    return TabTodos

  }

  if (tabActiva.value === 'electronica') {

    return TabElectronica

  }

  return TabPerifericos

})

</script>

<style scoped>

.botones {
  display: flex;
  gap: 10px;
  margin-bottom: 20px;
}

button {
  padding: 10px 15px;
  cursor: pointer;
}

</style>