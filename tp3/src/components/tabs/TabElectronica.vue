<template>

  <div>

    <h1>Productos de Electrónica</h1>

    <ListaProductos
      :productos="productosElectronica"
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

const productosElectronica =
  productos.filter(producto =>
    producto.categoria === 'Electrónica'
)

onMounted(() => {

  console.log('TabElectronica — montado')

})

onUnmounted(() => {

  console.log('TabElectronica — desmontado')

})

onActivated(() => {

  console.log('TabElectronica — activado')

})

onDeactivated(() => {

  console.log('TabElectronica — desactivado')

})

</script>

<style scoped>

h1 {
  margin-bottom: 20px;
}

</style>