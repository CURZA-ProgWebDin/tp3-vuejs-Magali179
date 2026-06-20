<template>

  <div>

    <h2>Lista de productos</h2>

    <p v-if="cargando">
      Cargando...
    </p>

    <div
      v-else
      ref="box"
      class="lista"
    >

      <!-- LISTA DINÁMICA -->

      <TarjetaProducto
        v-for="producto in productos"
        :key="producto.id"
      >

        <template #header>

          <h3>
            {{ producto.nombre }}
          </h3>

          <p>
            Categoría: {{ producto.categoria }}
          </p>

        </template>

        <template #body="{ expandida, toggleExpandir }">

          <p>
            Precio: ${{ producto.precio }}
          </p>

          <button @click="toggleExpandir">

            {{ expandida
              ? 'Ocultar stock'
              : 'Mostrar stock' }}

          </button>

          <p v-if="expandida">
            Stock: {{ producto.stock }}
          </p>

        </template>

      </TarjetaProducto>

      <hr />

      <h2>Ejemplos de Slots</h2>

      <!-- TARJETA 1 -->
  
      <TarjetaProducto>

        <template #header>

          <h3>Notebook Lenovo</h3>

        </template>

        <template #body="{ expandida, toggleExpandir }">

          <p>Precio: $850000</p>

          <button @click="toggleExpandir">

            {{ expandida
              ? 'Ocultar stock'
              : 'Mostrar stock' }}

          </button>

          <p v-if="expandida">
            Stock disponible: 12
          </p>

        </template>

        <template #footer>

          <button>
            Comprar
          </button>

        </template>

      </TarjetaProducto>

      <!-- TARJETA 2 -->
      <!-- usa fallback en footer-->

      <TarjetaProducto>

        <template #header>

          <h3>Mouse Logitech</h3>

        </template>

        <template #body="{ expandida, toggleExpandir }">

          <p>Precio: $48000</p>

          <button @click="toggleExpandir">

            {{ expandida
              ? 'Ocultar stock'
              : 'Mostrar stock' }}

          </button>

          <p v-if="expandida">
            Stock disponible: 30
          </p>

        </template>

      </TarjetaProducto>

      <!-- TARJETA 3 -->
      <!-- libre -->

      <TarjetaProducto>

        <template #header>

          <h3>Auriculares Sony</h3>

        </template>

        <template #body="{ expandida, toggleExpandir }">

          <button @click="toggleExpandir">

            {{ expandida
              ? 'Ver menos'
              : 'Ver más' }}

          </button>

          <div v-if="expandida">

            <p>Precio: $310000</p>

            <p>Stock: 5</p>

          </div>

        </template>

        <template #footer>

          <a href="#">
            Agregar a favoritos
          </a>

        </template>

      </TarjetaProducto>

    </div>

  </div>

</template>

<script setup>

import {
  ref,
  useTemplateRef,
  onMounted,
  onUpdated,
  onBeforeUnmount
} from 'vue'

import TarjetaProducto from './TarjetaProducto.vue'

const props = defineProps({
  productos: {
    type: Array,
    required: true
  }
})

const cargando = ref(true)

const box = useTemplateRef('box')

let timer = null

function esperar(ms) {

  return new Promise(resolve =>
    setTimeout(resolve, ms)
  )

}

async function cargarProductos() {

  cargando.value = true

  await esperar(800)

  cargando.value = false

}

onMounted(() => {

  cargarProductos()

  timer = setInterval(() => {

    cargarProductos()

  }, 30000)

})

onUpdated(() => {

  if (box.value) {

    box.value.scrollTop =
      box.value.scrollHeight

  }

})

onBeforeUnmount(() => {

  clearInterval(timer)

  console.log(
    'ListaProductos desmontado — polling detenido'
  )

})

</script>

<style scoped>

.lista {
  max-height: 700px;
  overflow-y: auto;
  border: 1px solid #ccc;
  padding: 20px;
}

button {
  margin-top: 10px;
  padding: 8px;
  cursor: pointer;
}

hr {
  margin: 40px 0;
}

</style>