<script setup>
import { ref } from 'vue';

// 1. Importación de datos
import jsonData from './data/datos.json';
const datos = ref(jsonData);
const misColores = datos.value.paleta;

// 2. Importación de componentes
import TituloKelsi from './componentes/TituloKelsi.vue';
import BloqueTipografia from './componentes/BloqueTipografia.vue';
</script>

<template>
  <div class="layout-libreta">
    
    <aside class="menu-lateral">
      <nav>
        <ul>
          <li><a href="#introduccion">Introducción</a></li>
          <li><a href="#color">Paleta de Color</a></li>
          <li><a href="#tipografia">Tipografía</a></li>
          <li><a href="#concepto">Concepto</a></li>
        </ul>
      </nav>
    </aside>

    <main class="contenido-principal">
      
      <section id="introduccion" class="seccion">
        <header>
          <TituloKelsi :texto="datos.info.titulo" />
          <p class="autores">Por: {{ datos.info.autores }}</p>
        </header>
        <div class="texto-introduccion">
          <p>{{ datos.introduccion.parrafo1 }}</p>
          <p>{{ datos.introduccion.parrafo2 }}</p>
        </div>
      </section>

      <section id="color" class="seccion">
        <TituloKelsi texto="Paleta de Color" />
        <div class="grid-colores">
          <div v-for="item in misColores" :key="item.hex" class="tarjeta-color">
            <div class="circulo" :style="{ backgroundColor: item.hex }"></div>
            <div class="texto-ficha">
              <strong>{{ item.nombre }}</strong>
              <p>{{ item.hex }}</p>
            </div>
          </div>
        </div>
      </section>

      <section id="tipografia" class="seccion">
        <TituloKelsi texto="Tipografía" />
        <BloqueTipografia 
          nombre="Kelsi Regular"
          familia="'Kelsi-Regular', sans-serif"
          descripcion="Tipografía principal para grandes titulares y logo."
        />
        <BloqueTipografia 
          nombre="Kelsi Fill"
          familia="'Kelsi-Fill', sans-serif"
          descripcion="Variante de relleno para el efecto de capas dinámico."
        />
      </section>

    </main>
  </div>
</template>

<style lang="scss">
@import './styles/main.scss';
@import './styles/variables';

.layout-libreta {
  display: flex;
  height: 100vh;
}

/* MENÚ LATERAL */
.menu-lateral {
  width: 250px;
  background-color: darken($bandcamp-beige, 5%); // Un tono más oscuro para el lomo
  border-right: 2px solid $bandcamp-negro;
  padding: 2rem 1rem;
  
  ul {
    list-style: none;
    padding: 0;
    
    li {
      margin-bottom: 1.5rem;
      a {
        text-decoration: none;
        color: $bandcamp-negro;
        font-weight: bold;
        transition: 0.3s;
        &:hover { color: $bandcamp-azul; }
      }
    }
  }
}

/* ÁREA DE CONTENIDO */
.contenido-principal {
  flex: 1;
  overflow-y: auto;
  padding: 4rem;
  background-color: $bandcamp-beige;
}

.seccion {
  min-height: 70vh;
  margin-bottom: 8rem;
}

.autores {
  font-style: italic;
  margin-bottom: 2rem;
}

/* GRID DE COLORES */
.grid-colores {
  display: flex;
  gap: 30px;
  flex-wrap: wrap;
  margin-top: 2rem;
}

.tarjeta-color {
  text-align: center;
  .circulo {
    width: 120px;
    height: 120px;
    border-radius: 50%;
    margin: 0 auto 10px;
    border: 3px solid $bandcamp-negro; // Toque cartoon/diseño
    box-shadow: 4px 4px 0px rgba(0,0,0,0.1);
  }
}
</style>