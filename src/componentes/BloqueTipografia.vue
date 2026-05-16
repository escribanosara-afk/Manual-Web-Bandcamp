<template>
  <div class="seccion-tipografia">
    <div class="contenedor-kelsi">
      <h2 class="kelsi-fill">Tipografía</h2>
      <h2 class="kelsi-outline">Tipografía</h2>
    </div>
    <p>Uso de las variantes Kelsi para el rediseño de Bandcamp.</p>
  </div>
</template>

<script setup>
// Aquí irá la lógica más adelante
</script>

<style scoped lang="scss">
.contenedor-kelsi {
  position: relative;
  height: 100px; /* Ajusta según vuestro diseño */
  
  h2 {
    position: absolute;
    top: 0;
    left: 0;
    margin: 0;
    font-size: 80px;
  }

  .kelsi-fill {
    font-family: 'Kelsi 1', sans-serif;
    color: #1da1f2; /* Azul Bandcamp o el vuestro */
    z-index: 1;
  }

  .kelsi-outline {
    font-family: 'Kelsi', sans-serif;
    z-index: 2;
    /* Este es el que hace el efecto de contorno si la tipo es outline */
  }
}
</style>