<template>
  <div id="app">
    <h1>Problema de Monty Hall</h1>
    <div class="inicio" v-if="!started">
      <label for="qtdPortas">Qtd Portas</label>
      <input type="text" name="qtdPortas" id="qtdPortas" class="texto" v-model.number="portsAmount"/>
      <label for="portaCerta">Porta certa</label>
      <input type="text" name="portaCerta" id="portaCerta" class="texto" v-model.number="selectedPort"/>
      <button class="botao" @click="started = true">INICIAR</button>
    </div>
    <button v-if="started" @click="started = false">REINICIAR</button>
    <div class="doors" v-if="started">
      <div v-for="i in portsAmount" :key="i">
        <Porta :num="i" :hasPresente="i === selectedPort"/> <!-- se for sem os dois pontos... ele interpreta uma string e não um boolean -->
      </div>
    </div>
  </div>
</template>

<script>
import Porta from './components/Porta.vue'

export default {
  name: "App",
  components: {Porta},
  data: function (){
    return {
      started: false,
      portsAmount: 3,
      selectedPort: null
    }
  }
};
</script>

<style>
body {
  margin: 0;
  font-family: Helvetica;
}
.inicio {
  border: 1px solid yellow;
  border-radius: 10px;
  padding: 20px;
  display: grid;
  grid-template-rows: 40px 40px 40px;
}
.texto {
  margin-left: 10px;
  width: 5em;
}
.botao {
  grid-column: span 2;
}
#app {
  display: flex;
  flex-direction: column;
  height: 100vh;
  /* justify-content: center; */
  align-items: center;
  color: white;
  background-color: rgb(39, 39, 39);
}
.doors {
  margin-top: 10px;
  align-self: stretch;
  display: flex;
  justify-content: space-around;
  flex-wrap: wrap;
}
</style>
