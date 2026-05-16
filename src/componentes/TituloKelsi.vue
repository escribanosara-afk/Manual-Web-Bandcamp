<template>
  <div class="titulo-capas">
    <!-- Capa 1: El relleno -->
    <span class="texto-relleno" aria-hidden="true">{{ texto }}</span>
    
    <!-- Capa 2: El contorno (queda por encima) -->
    <span class="texto-contorno">{{ texto }}</span>
  </div>
</template>

<script setup>
defineProps({
  texto: {
    type: String,
    required: true
  }
})
</script>

<style scoped lang="scss">
.titulo-capas {
  position: relative;
  display: inline-block; 
  font-size: 4rem; 
  line-height: 1; 
}

.texto-contorno {
  font-family: 'Kelsi-Regular', sans-serif;
  position: relative; 
  z-index: 2; 
  color: #000000;
}

.texto-relleno {
  font-family: 'Kelsi-Fill', sans-serif;
  position: absolute; 
  top: 0;
  left: 0;
  z-index: 1; 
  color: #62B8F6; 
}
</style>