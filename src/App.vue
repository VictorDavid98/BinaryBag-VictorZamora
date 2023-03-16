<template>
  <img width="300" src="./assets/navbar_logo.955ebbbb.jpg" />

  <nav class="navbar">
    <ul>
      <button class="botonNav" @click="showComponent = 'ActividadA'">
        Robot
      </button>
      <button class="botonNav" @click="showComponent = 'ActividadB'">
        Amigo en Común 
      </button>
      <button class="botonNav" @click="showComponent = 'ActividadC'">
        Palabra más Frecuente
      </button>
      <button class="botonNav" @click="showComponent = 'ActividadD'">
        Recaudación de Eventos
      </button>
    </ul>
  </nav>
  <div v-show="showComponent === 'ActividadA'">
    <ActividadA />
  </div>
  <div v-show="showComponent === 'ActividadB'">
    <ActividadB />
  </div>
  <div v-show="showComponent === 'ActividadC'">
    <ActividadC />
  </div>
  <div v-show="showComponent === 'ActividadD'">
    <ActividadD />
  </div>
</template>

<script>
import ActividadA from "./components/ActividadA.vue";
import ActividadB from "./components/ActividadB.vue";
import ActividadC from "./components/ActividadC.vue";
import ActividadD from "./components/ActividadD.vue";

export default {
  name: "App",
  components: {
    ActividadA,
    ActividadB,
    ActividadC,
    ActividadD,
  },
  data() {
    return {
      showComponent: "ActividadA",
    };
  },
  methods: {
    // Este método se ejecuta cuando se hace clic en un botón del navbar
    // y establece el componente a mostrar en base al valor del botón
    showSelectedComponent(componentName) {
      this.showComponent = componentName;
    },
  },
};
</script>

<style>
#app {
  font-family: "Times New Roman", Times, serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 30px;
}
.navbar {
  background-color: #fff;
  border-top: 4px solid #0b8043;
  border-bottom: 4px solid #0b8043;
  height: auto;
  width: 100%;
  align-items: center;
  justify-content: center;
}

.navbar ul {
  display: flex;
  justify-content: space-around;
}
.navbar a {
  font-size: 25px;
  text-decoration: none;
  color: #000000;
}
.botonNav {
  font-family: "Times New Roman", Times, serif;
  background-color: white;
  border: none;
  color: #0b8043;
  padding: 12px 12px;
  text-align: center;
  text-decoration: none;
  font-size: 25px;
}
</style>
