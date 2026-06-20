<template>
   <div class="tarjeta">

    <div class="header">
      <slot name="header"></slot>
    </div>

    <div class="body">

  <slot
    name="body"
    :expandida="expandida"
    :toggleExpandir="toggleExpandir"
  ></slot>

</div>

    <div class="footer">
      <slot name="footer">
        <span>Sin acciones disponibles</span>
      </slot>
    </div>

  </div>
</template>

<script setup>
import { ref } from 'vue'

const expandida = ref(false)

function toggleExpandir() {
  expandida.value = !expandida.value
}
</script>

<style scoped>
.tarjeta {
  border: 1px solid #ccc;
  border-radius: 10px;
  padding: 16px;
  margin-bottom: 20px;
  background: #f9f9f9;
}

.header {
  margin-bottom: 10px;
}

.body {
  margin-bottom: 10px;
}

.footer {
  border-top: 1px solid #ddd;
  padding-top: 10px;
}
</style>