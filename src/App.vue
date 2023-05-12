<script setup>

import { ref } from 'vue'

const produtos = ref([
  {
    id: 1,
    nome: 'Bruxa Maravilha',
    Galeoẽs: 6,
    quantidade: 0,
    img: 'https://cdn.create.vista.com/api/media/small/16332707/stock-photo-love-potion'
  },
  {
    id: 2,
    nome: 'Caramelo Incha-Língua',
    Galeoẽs: 2,
    quantidade: 0,
    img: 'https://nerdicesemserie.files.wordpress.com/2015/03/m4.png'

  },
  {
    id: 3,
    nome: 'Chapéu-Escudo',
    Galeoẽs: '7',
    quantidade: 0,
    img: 'https://d1a87ut6isnmlv.cloudfront.net/thumb-img//PGYGIOvnXRfNSxpfhfSjk7vNHx8=/664x903:1882x2274/328x369/filters:watermark(/ca_logo.png,center,5,10)/produtos/7e/e4/M2439_ZYaszbJ.jpg'
  },
  {
    id: 4,
    nome: 'Chapéu Anti-Gravidade',
    Galeoẽs: 3,
    quantidade: 0,
    img: 'https://2.bp.blogspot.com/-kQmR8O4wYU0/WMAFPVmt-vI/AAAAAAAAky0/9x82KpFJssYgsEWq5uUOTOJHke1p527MwCLcB/s320/6-2-hat-png-images.png'
  },
  {
    id: 5,
    nome: 'Infalível Removedor de Espinhas em Dez Segundos',
    Galeoẽs: 5,
    quantidade: 0,
    img: 'https://dygtyjqp7pi0m.cloudfront.net/i/37733/32592908_1.jpg?v=8D69D936C9CC2B0'
  },
  {
    id: 6,
    nome: 'Fantasias Debilitantes',
    Galeoẽs: 4,
    quantidade: 0,
    img: 'https://2.bp.blogspot.com/-aN7cGpRluHw/Ub2_bV4pemI/AAAAAAAAEMs/okSqx2iyM4A/s1600/decoy_box_label_top_by_jhadha-d4zb8g0.png'

  },
  {
    id: 7,
    nome: 'Orelhas Extensíveis',
    Galeoẽs: 10,
    quantidade: 0,
    img: 'https://quenembanana.com/wp-content/uploads/Extensor-de-Orelha-Harry-Potter.jpg'
  },
  {
    id: 8,
    nome: 'Fogos Espontâneos Weasley',
    Galeoẽs: 13,
    quantidade: 0,
    imagem: 8,
    img: 'https://www.pngmart.com/files/15/Sparkle-Gold-Fireworks-PNG-Transparent-Image.png'
  },
  {
    id: 9,
    nome: 'Kit Mata-Aula',
    Galeoẽs: 15,
    quantidade: 0,
    img: 'https://pm1.narvii.com/6308/05165531038ae65313fbd0daf325674010f59e84_00.jpg'
  },
  {
    id: 10,
    nome: 'Vomitilha',
    Galeoẽs: 2,
    quantidade: 0,
    img: 'https://becodiagonal-hms.weebly.com/uploads/1/0/6/7/10674278/7434457.png?198'

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
function totalvalor() {
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
  <h1 class="titulo">Gemialidades Weasley</h1>
  <div class="produtos">

    <div v-for="(item, index) in produtos" :key="index" class="produto">
      <p> Item: {{ item.nome }}</p>
      <p> Quantidade: {{ item.quantidade }} </p>
      <p>Galeoẽs: {{ (item.Galeoẽs) }}</p>
      <div class="imagem-acoes">
        <img :src="item.img" class="img" width="200" height="200">
        <div class="acoes" text-align="right">
          <button @click="incrementar(index)">+</button>
          <button @click="descrementar(index)">-</button>
          <button @click="addcarrinho(item)">adicionar</button>
        </div>
      </div>
    </div>
  </div>

  <ul>
    <div class="carrinho">
      <h1>Carrinho</h1>
      <ul>
        <li v-for="(item, index) in carrinho" :key="index">{{ item.nome }}
          <p> valor: {{ (item.Galeoẽs) }} Galeoẽs</p>
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
.produtos {
  display: flex;
  flex-wrap: wrap;
}

.produto {
  margin: 20px;
  width: 30%;
}

.imagem-acoes {
  display: flex;
  margin-right: 10px;
}

.acoes {
  display: flex;
  flex-direction: column;
  justify-content: center;
  margin-left: 30px;
}

li {
  display: grid;
  grid-template-columns: 1fr 1fr;
  padding: 10px;
}

button {
  height: 30px;
  width: 140px;
  border-radius: 10px;
  border: none;
  margin-top: 10px;
  color: rgb(255, 255, 255);
  background-color: rgba(238, 49, 15, 0.473);
  margin-right: 10px;


}

#remove {
  border: none;
  background-color: rgba(131, 141, 141, 0.589);
}

.letraTotal {
  color: rgb(41, 16, 131);
}

.img {
  border-radius: 50px;
  margin-left: 10px;
}

.titulo {
  text-align: center;
  color: rgb(165, 71, 42);
}
</style>