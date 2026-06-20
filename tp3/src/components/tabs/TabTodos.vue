<template>

  <div>

    <h1>Todos los productos</h1>

    <ListaProductos
      :productos="productos"
    />

  </div>

</template>

<script setup>

import {
  onMounted,
  onUnmounted,
  onActivated,
  onDeactivated
} from 'vue'

import ListaProductos
from '../ListaProductos.vue'

import {
  productos
} from '../../data/productos'

onMounted(() => {

  console.log('TabTodos — montado')

})

onUnmounted(() => {

  console.log('TabTodos — desmontado')

})

onActivated(() => {

  console.log('TabTodos — activado')

})

onDeactivated(() => {

  console.log('TabTodos — desactivado')

})

</script>

<style scoped>

h1 {
  margin-bottom: 20px;
}

</style>