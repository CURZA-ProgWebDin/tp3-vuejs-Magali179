<template>

  <div>

    <h1>Productos Periféricos</h1>

    <ListaProductos
      :productos="productosPerifericos"
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

const productosPerifericos =
  productos.filter(producto =>
    producto.categoria === 'Periféricos'
)

onMounted(() => {

  console.log('TabPerifericos — montado')

})

onUnmounted(() => {

  console.log('TabPerifericos — desmontado')

})

onActivated(() => {

  console.log('TabPerifericos — activado')

})

onDeactivated(() => {

  console.log('TabPerifericos — desactivado')

})

</script>

<style scoped>

h1 {
  margin-bottom: 20px;
}

</style>