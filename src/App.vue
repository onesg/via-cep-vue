<template>
  <img alt="Vue logo" src="./assets/logo.png">

  <h1>Usando via CEP</h1>

  <label for="cep">CEP </label>
  <input type="text" name="cep" id="cep" v-model="cep"> <!-- VINCULANDO INPUT AO OBJETO CEP -->
  <button @click="buscarCep">Pesquisar</button> <!-- EVENTO CLICK PARA CHAMAR O METODO -->

</template>

<script>
// IMPORTACOES
import axios from "axios";  // ADICIONADO INSTANCIA AXIOS AO PROJETO

export default {
  name: 'App',
  data(){
    return{
      cep: '15780000',
    }
  },
  // DEFININDO OBJETO METHODS
  methods: {
    buscarCep(){
      axios({ // USA INSTANCIA AXIOS
        method: 'get',
        url: `https://viacep.com.br/ws/${this.cep}/json`,
        responseType: 'json'
      }).then( (response) => {
        console.log(response.data);
        }); // THEN E QUANDO VEM A REPOSTA
    }
  }
}
</script>

<style>
  body{
    background-color: white;
  }
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
