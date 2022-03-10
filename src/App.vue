<template>
  <img alt="Vue logo" src="./assets/logo.png">

  <h1>Usando via CEP</h1>

  <label for="cep">CEP </label>
  <input type="text" name="cep" id="cep" v-model="cep"> <!-- VINCULANDO INPUT AO OBJETO CEP -->
  <button>Pesquisar</button>

</template>

<script>



export default {
  name: 'App',
  data(){
    return{
      cep: '15780000',

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
