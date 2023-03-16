<template>
  <div class="container-robot">
    <h1>ROBOT</h1>
    <label for="instrucciones">Instrucciones:</label>
    <input
      type="text"
      v-model="instrucciones"
      id="instrucciones"
      @keydown="checkKey($event)"
    />
    <button class="boton" @click="vuelve()" id="calcular">Calcular</button>
    <button class="boton" @click="limpiar()">Limpiar</button>
    <p class="resultado">
      El robot vuelve a su posicion: <span>{{ resultado }}</span>
    </p>
    <br />
    <p>pd: Se puede hacer el calculo con "D" y "I" mayuscula y minuscula ;)</p>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  data() {
    return {
      instrucciones: "",
      resultado: "",
    };
  },
  methods: {
    vuelve() {
      let x = 0;
      let y = 0;
      for (let i = 0; i < this.instrucciones.length; i++) {
        if (this.instrucciones[i] === "I" || this.instrucciones[i] === "i") {
          x--;
        } else if (
          (this.instrucciones[i] === "D") |
          (this.instrucciones[i] === "d")
        ) {
          x++;
        }
      }
      if (x === 0 && y === 0) {
        this.resultado = "verdadero";
      } else {
        this.resultado = "falso";
      }
    },
    limpiar() {
      this.instrucciones = "";
    },
    checkKey(event) {
      const key = event.keyCode || event.charCode;
      if (key === 73 || key === 68) {
        return true;
      }

      event.preventDefault();
      return false;
    },
  },
};
</script>

<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
label {
  margin-right: 10px;
  font-size: 25px;
}
input {
  border: 1px solid #0b6629;
  height: 25px;
  width: 200px;
  border-radius: 5px;
}

.boton {
  background-color: white;
  border: 1px solid #0b6629;
  border-radius: 5px;
  margin-left: 10px;
  font-size: 15px;
  padding: 5px 20px;
}
.resultado {
  font-family: "Times New Roman", Times, serif;
  font-size: 30px;
  font-weight: 500;
}
</style>
