<script setup>
import { computed, reactive, watch } from 'vue';

const estado = reactive({
  operacao: "",
  campo1: 0,
  campo2: 0,
  resultado: 0,
  realizarOperacao: false,
})

function adicao(){
  estado.operacao = "+";
  if(estado.campo1 !== 0 && estado.campo2 !== 0){
    executarOperacao();
  } else{
    estado.realizarOperacao = false;
  }
}

function subtracao(){
  estado.operacao = "-";
  if(estado.campo1 !== 0 && estado.campo2 !== 0){
    executarOperacao();
  } else{
    estado.realizarOperacao = false;
  }
}

function multiplicacao(){
  estado.operacao = "x";
  if(estado.campo1 !== 0 && estado.campo2 !== 0){
    executarOperacao();
  } else{
    estado.realizarOperacao = false;
  }
}

function divisao(){
  estado.operacao = "/";
  if(estado.campo1 !== 0 && estado.campo2 !== 0){
    executarOperacao();
  } else{
    estado.realizarOperacao = false;
  }
}

function executarOperacao() {
  switch (estado.operacao) {
    case "+":
      estado.resultado = Number(estado.campo1) + Number(estado.campo2);
      break;
    case "-":
      estado.resultado = Number(estado.campo1) - Number(estado.campo2);
      break;
    case "x":
      estado.resultado = Number(estado.campo1) * Number(estado.campo2);
      break;
    case "/":
      estado.resultado = Number(estado.campo1) / Number(estado.campo2);
      break;
    default:
      estado.resultado = 0;
  }
  estado.realizarOperacao = true;
}

</script>

<template>
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Roboto&display=swap" rel="stylesheet">
  <div class="container">
    <div class="visor">
    <h1>Calculadora Aritmética</h1>
    <p class="instrucoes">Para calcular, insira os valores e clique na operação que deseja. O cálculo é feito automaticamente.</p>
    <div class="conteudo">
      <div class="operacoes">
        <button @click="adicao"><img src="./media/math-plus.svg"></button>
        <button @click="subtracao"><img src="./media/math-minus.svg"></button>
        <button @click="multiplicacao"><img src="./media/math-multiply.svg"></button>
        <button @click="divisao"><img src="./media/math-divide.svg"></button>
      </div>
      <label for="campo-numero1">Valor 1</label>
      <input @keyup="ecampo1 => estado.campo1 = ecampo1.target.value" id="campo-numero1" type="number" v-model="campo1"><br>
      <p v-if="estado.operacao" class="operacao-numeros">{{ estado.operacao }}</p>
      <label for="campo-numero2">Valor 2</label>
      <input @keyup="ecampo2 => estado.campo2 = ecampo2.target.value" id="campo-numero2" type="number" v-model="campo2">

    </div>
    <div v-if="estado.realizarOperacao">
      <h1 class="resultado">Resultado: {{ estado.resultado }}</h1>
    </div>
  </div>
  </div>
  <footer>
    <div class="footer">
    <p>por Nicollas Prudencio</p>
</div>

  </footer>
</template>

<style scoped>

.instrucoes{
  margin-bottom: 10px;
}

.container{
  height: 100%;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

.visor {
  background-color: #FFF;
  max-width: 500px;
  width: 500px;
  max-height: 300px;
  border-radius: 5px;
  text-align: center;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  align-items: center;
  padding-top: 10px;
  padding-bottom: 15px;
}

h1 {
  font-family: 'Roboto', sans-serif;
}

.operacoes {
  margin: 0 auto;
  max-width: 300px;
  display: flex;
  justify-content: space-between;
  margin-bottom: 30px;

}

label{
    font-family: 'Roboto', sans-serif;
}

#campo-numero1, #campo-numero2{
  margin-left: 10px;
}

img {
  height: 40px;
}

.operacao-numeros{
  height: 20px;
  width: 30px;
  margin-top: 5px;
  margin: 10px auto;
  font-weight: bold;
  font-size: 20px;
}

.resultado {
  margin-top: 10px;
  width: 100%;
  font-size: 30px;
}
.footer{
  position: fixed;
  bottom: 0;
  width: 100%;
  background-color: #f1f1f1;
  text-align: center;
  padding: 10px;
  font-family: 'Roboto', sans-serif;
}

</style>

<style>

*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body{
  background-color: #55324a;
}

#app {
  height: 100vh;
  width: 100vw;
}

</style>