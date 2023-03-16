<template>
  <div class="container-c">
    <div class="contenido">
      <h1>Palabra mas frecuente</h1>
      <textarea v-model="texto" placeholder="Ingrese un texto"></textarea>
      <input
        type="text"
        v-model="palabrasIgnoradas"
        placeholder="Palabras a ignorar separadas por comas"
      />
      <button @click="encontrarPalabraMasFrecuente()">
        Encontrar palabra más frecuente
      </button>
      <p v-if="palabraMasFrecuente">
        La palabra más frecuente es: {{ palabraMasFrecuente }}
      </p>
      <p v-else>No se encontró una palabra más frecuente.</p>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      texto: "",
      palabrasIgnoradas: "",
      palabraMasFrecuente: "",
    };
  },
  methods: {
    encontrarPalabraMasFrecuente() {
      const textoMinusculas = this.texto.toLowerCase();
      const palabrasIgnoradas = this.palabrasIgnoradas
        .split(",")
        .map((p) => p.trim().toLowerCase());

      const palabras = textoMinusculas.replace(/[^\w\s]/gi, "").split(/\s+/);
      const contadorPalabras = {};

      palabras.forEach((palabra) => {
        if (!palabrasIgnoradas.includes(palabra)) {
          if (contadorPalabras[palabra]) {
            contadorPalabras[palabra]++;
          } else {
            contadorPalabras[palabra] = 1;
          }
        }
      });

      let palabraMasFrecuente = null;
      let contadorMaximo = 0;

      for (const [palabra, contador] of Object.entries(contadorPalabras)) {
        if (contador > contadorMaximo) {
          palabraMasFrecuente = palabra;
          contadorMaximo = contador;
        }
      }

      this.palabraMasFrecuente = palabraMasFrecuente;
    },
  },
};
</script>

<style>
.container-c {
  width: 100%;
  display: flex;
  justify-content: center;
}
.contenido {
  width: 50%;
  display: flex;
  flex-direction: column;
  justify-items: center;
  align-items: center;
  align-content: center;
}
.contenido textarea {
  width: 600px;
  border: 1px solid #068d01;
  height: 70px;
  margin-bottom: 10px;
}
.contenido input {
  width: 600px;
  border: 1px solid #068d01;
  margin-bottom: 20px;
}
.contenido button {
  width: 400px;
  border: 2px solid #068d01;
  border-radius: 10px;
  background-color: white;
  color: #068d01;
  font-size: 20px;
  padding: 5px;
}
</style>
