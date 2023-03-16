<template>
  <div>
    <h2>Comprobar amigos en común</h2>
    <p>¿Tienen las personas</p>
    <input type="text" v-model="i" /> y <input type="text" v-model="j" />
    <p>un amigo en común?</p>
    <button @click="comprobarAmigos">Comprobar</button>
    <p v-if="resultado">Sí tienen un amigo en común</p>
    <p v-else>No tienen un amigo en común</p>
  </div>

  <img src="../assets/grafo.png" alt="" />
</template>

<script>
export default {
  data() {
    return {
      n: 5, // número de personas
      amistades: [
        [false, true, false, true, false],
        [true, false, true, false, false],
        [false, true, false, false, true],
        [true, false, false, false, true],
        [false, false, true, true, false],
      ],
      i: null, // primera persona
      j: null, // segunda persona
      resultado: false, // resultado de la comprobación
    };
  },
  methods: {
    comun(i, j) {
      if (i === j) {
        // evitar llamadas con parámetros idénticos
        throw new Error("Los parámetros no pueden ser idénticos");
      }
      for (let k = 0; k < this.n; k++) {
        // iterar sobre todas las personas
        if (this.amistades[i][k] && this.amistades[j][k]) {
          // si existe una tercera persona k que tenga amistad tanto con i como con j
          return true; // devolver verdadero
        }
      }
      return false; // si no se encontró una tercera persona k, devolver falso
    },
    comprobarAmigos() {
      try {
        this.resultado = this.comun(this.i - 1, this.j - 1); // restar 1 para ajustar a los índices del arreglo
      } catch (e) {
        alert(e.message); // manejar excepciones
      }
    },
  },
};
</script>
<style>
input {
  width: 50px;
}
</style>
