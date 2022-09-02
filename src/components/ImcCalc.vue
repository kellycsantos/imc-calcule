<template>
  <div class="hello">
    <div class="input-container">
      <label>Informe seu peso:</label>
      <input type="text" v-model="weight" placeholder="Exemplo: 43.1" />
      <label>Informe sua altura em metros:</label>
      <input type="text" v-model="height" placeholder="Exemplo: 1.63" />
      <input type="submit" @click="calcImc" />
      <span v-if="erro"
        >Infome seus dados somente com numeros seguindo os exemplos</span
      >

      <div
        v-if="imcIndices !== null && !erro"
        :style="`background:${imcIndices.color}`"
        class="imcResults"
      >
        <h2>IMC {{ imcIndices.imc }}</h2>
        <p>{{ imcIndices.description }}</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "ImcCalc",
  data() {
    return {
      weight: null,
      height: null,
      result: null,
      imcIndices: null,
      erro: false,
    };
  },
  methods: {
    calcImc() {
      const calc = this.weight / (this.height * this.height);
      this.result = calc.toFixed(2);
      this.indiceImc(this.result);
    },
    indiceImc(imc) {
      if (imc < 18) {
        this.imcIndices = {
          imc: imc,
          description: "Você está abaixo do peso",
          color: "#f0c757",
        };
        this.erro = false;
      } else if (imc <= 25) {
        this.imcIndices = {
          imc: imc,
          description: "Atualmente o seu peso está dentro do saudável.",
          color: "#7eb41a",
        };
        this.erro = false;
      } else if (imc > 25) {
        this.imcIndices = {
          imc: imc,
          description: "Você está acima, tente procurar um especialista.",
          color: "#b41a1a",
        };
        this.erro = false;
      } else {
        this.erro = true;
      }
    },
  },
};
</script>

<style scoped>
h2,
p {
  margin: 2px 0;
  padding: 0;
}
.input-container {
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 50px 0;
}
.input {
  margin: 10px;
}
input {
  border: 1px solid #ea5f9d;
  border-radius: 5px;
  outline: none;
  background: transparent;
  color: white;
  height: 5vh;
  padding: 5px;
  font-size: 1.2rem;
  text-align: center;
  margin: 8px 0;
}
input[type="submit"] {
  border: 1px solid #ea5f9d;
  border-radius: 4px;
  height: 7vh;
  outline: none;
  background: #ea5f9d;
  width: 20vw;
  color: #ffffff;
  padding: 7px;
  text-align: center;
  cursor: pointer;
}

.imcResults {
  width: 50vw;
  border-radius: 10px;
  padding: 15px 0;
  margin-top: 25px;
}

@media screen and (min-width: 768px) {
  label {
    font-size: 0.9rem;
  }
  input {
    height: 5vh;
    width: 45vw;
    font-size: 1rem;
  }
  input[type="submit"] {
    height: 5vh;
  }
  .imcResults {
    width: 25vw;
    border-radius: 10px;
    padding: 15px 0;
  }
}

@media screen and (min-width: 1280px) {
  label {
    font-size: 2.2rem;
  }
  input {
    height: 7vh;
    width: 32vw;
    font-size: 2.5rem;
  }
  input[type="submit"] {
    height: 6vh;
  }
  .imcResults {
    width: 30vw;
    border-radius: 10px;
    padding: 15px 0;
    font-size: 2rem;
  }
}
</style>
