<template>
  <img alt="Vue logo" src="./assets/logo.png">

  <h1>Usando via CEP</h1>

  <label for="cep">CEP </label>
  <input type="text" name="cep" id="cep" v-model="cep" placeholder="Exemplo: 15780000" autofocus> <!-- VINCULANDO INPUT AO OBJETO CEP -->
  <button @click="buscarCep">Pesquisar</button> <!-- EVENTO CLICK PARA CHAMAR O METODO -->

  <hr>

  <p><strong>Cidade: </strong>{{dadosCep.cidade}}/{{dadosCep.uf}}</p>
  <p><strong>Bairro: </strong>{{dadosCep.bairro}}</p>
  <p><strong>Logradouro: </strong>{{dadosCep.logradouro}}</p>

</template>

<script>
// IMPORTACOES
import axios from "axios";  // ADICIONADO INSTANCIA AXIOS AO PROJETO

export default {
  name: 'App',
  data(){
    return{
      cep: '',
      // DECLARANDO OBJETO dadosCep
      dadosCep: {
        cep: '',
        cidade: '',
        uf: '',
        bairro: '',
        logradouro: '',
      }
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
        //console.log(response.data);
        this.mostrarDados(response.data); // 
        }); // THEN E QUANDO VEM A REPOSTA
    },
    mostrarDados(dados){
      // mostrarDados IRA PEGAR DADOS DA RESPOSTA E ALIMENTA O dadosCep
      this.dadosCep.cep = dados.cep;
      this.dadosCep.cidade = dados.localidade;
      this.dadosCep.uf = dados.uf;
      this.dadosCep.bairro = dados.bairro;
      this.dadosCep.logradouro = dados.logradouro;
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
