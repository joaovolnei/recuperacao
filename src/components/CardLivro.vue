<script setup>
import { adicionarAoCarrinho } from '@/_data/carrinho.js'
import MButton from './MButton.vue'
import CartPlus from 'vue-material-design-icons/CartPlus.vue'
import ShareVariant from 'vue-material-design-icons/ShareVariant.vue'


const props = defineProps({ livro: Object })

function formatarPreco(preco) {
  return 'R$ ' + preco.toFixed(2).replace('.', ',')
}
</script>

<template>
  <div class="card-livro">
    <div class="card-info-livro">
      <div class="wrap-livro">
        <img :src="props.livro.img" alt="Capa do livro" class="capa-livro" />
      </div>
      <hr />
      <p class="titulo-livro">{{ props.livro.title }}</p>
      <p class="autor-livro">{{ props.livro.author }}</p>
      <p class="preco-livro">{{ formatarPreco(props.livro.price) }}</p>
    </div>
    <div class="card-buttons-livros">
      <hr />
      <m-button class="secundario" @click="adicionarAoCarrinho(props.livro)" text="Add" />
      <cart-plus />
      <m-button class="estrela" text="&#9734;" />
      <m-button class="sucesso"> <share-variant /> </m-button>
    </div>
  </div>
</template>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Bruno+Ace+SC&family=Mukta&family=Press+Start+2P&display=swap');
.card-livro {
  margin: 5px 10px;
  padding: 10px;
  background-color: rgb(2, 88, 88);
  border-radius: 10px;
  border-style:groove;
  width: 180px;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  font-family: 'Mukta', sans-serif;
  font-size: 17px;
  border-width: 7px;
}

.estrela:hover {
  transition:0.5s;
  color: yellow;
}

button:hover {
  transition: 0.6s;
  color: red;
}
.wrap-livro {
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: white;
  border-radius: 10px;
  width: 180px;
  height: 270px;
}
.capa-livro {
  width: 90%;
  max-height: 100%;
}

.card-livro p {
  margin: 0;
  color: white;
}

.card-livro .titulo-livro {
  font-weight: bold;
  margin-bottom: 5px;
  color: white;
}
hr {
  border-radius: 2px;
  border-style: groove;
}
</style>
