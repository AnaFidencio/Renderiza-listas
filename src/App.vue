<script setup>

import { ref } from 'vue'

const produtos = ref([
  {
    id: 1,
    nome: 'Bruxa Maravilha',
    Galeoẽs: 6,
    quantidade: 0,
  },
  {
    id: 2,
    nome: 'Caramelo Incha-Língua',
    Galeoẽs: 2,
    quantidade: 0,
  },
  {
    id: 3,
    nome: 'Chapéu-Escudo',
    Galeoẽs: '7',
    quantidade: 0,
  },
  {
    id: 4,
    nome: 'Chapéu Anti-Gravidade',
    Galeoẽs: 3,
    quantidade: 0,
  },
  {
    id: 5,
    nome: 'Infalível Removedor de Espinhas em Dez Segundos',
    Galeoẽs: 5,
    quantidade: 0,
  },
  {
    id: 6,
    nome: 'Fantasias Debilitantes',
    Galeoẽs: 4,
    quantidade: 0,
  },
  {
    id: 7,
    nome: 'Orelhas Extensíveis',
    Galeoẽs: 10,
    quantidade: 0,
  },
  {
    id: 8,
    nome: 'Fogos Espontâneos Weasley',
    Galeoẽs: 13,
    quantidade: 0,
  },
  {
    id: 9,
    nome: 'Kit Mata-Aula',
    Galeoẽs: 15,
    quantidade: 0,
  },
  {
    id: 10,
    nome: 'Vomitilha',
    Galeoẽs: 2,
    quantidade: 0,
  }
])

function incrementar(index) {
  produtos.value[index].quantidade++
}
function descrementar(index) {
  produtos.value[index].quantidade--
}
let valortotal = ref(0)

let carrinho = ref([])
function addcarrinho(item) {
  carrinho.value.push({
    codigo: item.id,
    nome: item.nome,
    Galeoẽs: item.Galeoẽs,
    quantidade: item.quantidade,
    totalitem: item.Galeoẽs * item.quantidade
  })
  totalvalor()
  item.quantidade = 1
}
function totalvalor(){
  for (let contador = 0; contador < carrinho.value.length; contador++) {
    valortotal.value = valortotal.value + carrinho.value[contador].totalitem  
  }
}
function limpacarrinho() {
  carrinho.value = []
}
function remover(index) {
  carrinho.value.splice(index, 1)
}
</script>

<template>
    <li v-for="(item, index) in produtos" :key="index">Item: {{ item.nome }} 
      <div></div>
      <p>
      Galeoẽs: {{ (item.Galeoẽs) }}
    </p>
    <p></p>
      Quantidade: {{ item.quantidade }}
      <button @click="incrementar(index)">+</button>
      <p></p>
      <button @click="descrementar(index)">-</button>
       <p></p>
        <button @click="addcarrinho(item)">adicionar</button>
    </li>

  <ul>
    <div class="carrinho">
    <h1>Carrinho</h1> 
    <ul>
      <li v-for="(item, index) in carrinho" :key="index">{{ item.nome }} 
      <p> valor: {{(item.Galeoẽs) }} Galeoẽs</p>
    <p>Quant: {{ item.quantidade }}</p>
    <button id="remove" @click="remover(index)">remover item</button>  
    <p class="letraTotal">Total de Galeoẽs: {{ (item.totalitem) }}</p>
    
   
      </li>
    </ul>
    <button @click="limpacarrinho()">limpar carrinho</button>
  </div>
</ul>
  
</template>

<style scoped>
li{
  display: grid;
  grid-template-columns:1fr 1fr;
  padding: 10px;
}
button{
  height: 30px;
  width: 140px;
  border-radius: 10px;
  border: none;
  margin-top: 10px;
  color: rgb(255, 255, 255);
  background-color: rgba(238, 49, 15, 0.473);
 
}
#remove{
  border:none;
  background-color: rgba(131, 141, 141, 0.589);
}
.letraTotal{
  color: rgb(41, 16, 131);
}


</style>