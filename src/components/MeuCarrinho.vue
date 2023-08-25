<script setup>
import { carrinho, removerItemCarrinho, atualizaQuantidadeItem } from '@/_data/carrinho.js'
import MButton from './MButton.vue'
import MMessage from './MMessage.vue';

function formatarPreco(preco) {
  return 'R$ ' + preco.toFixed(2).replace('.', ',')
}
</script>

<template>
  <div class="carrinho">
    <h2>Meu carrinho</h2>
    <hr />
    <div class="wrap-carrinho">
      <m-message v-if="carrinho.itens.length === 0"/>
      <div v-else>
        <div class="item-carrinho" v-for="(item, index) in carrinho.itens" :key="index">
          <div class="info-livro">
            <div class="imagem-livro">
              <img :src="item.img" class="icon-capa-livro" />
            </div>
            <div class="detalhes-livro">
              <div>
                <p>{{ item.title }}</p>
                <p class="info-livro-preco">{{ formatarPreco(item.price) }}/un</p>
              </div>
              <div>
                <p>
                  Quantidade:
                  <input
                    type="number"
                    v-model="item.quantidade"
                    @change="atualizaQuantidadeItem(item)"
                    min="1"
                  />
                </p>
                <button @click="removerItemCarrinho(item)">&#128465;</button>
                <p>Total: {{ formatarPreco(item.total) }}</p>
              </div>
            </div>
          </div>
        </div>
      </div>
      <m-button text="Clear" />
      <m-button text="Close"/>
      <m-button text="Favorites"/>
      <m-button text="Keep Buying"/>

      <p class="carrinho-total">Total: {{ formatarPreco(carrinho.total) }}</p>
    </div>
  </div>
</template>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Bruno+Ace+SC&family=Mukta&family=Press+Start+2P&display=swap');
.carrinho{
background-color: rgb(2, 88, 88);
border-radius: 4px;
border-width: 7px;
border-color: white;
border-style: groove;
text-align: center;
}

h2{
    font-family: 'Bruno Ace SC', cursive;
    color: white;
}
.wrap-carrinho .carrinho-total {
  position: relative;
  bottom: 3%;
  font-size: 1.5rem;
  font-weight: bold;
  font-family: 'Bruno Ace SC', cursive;
  color: white;
}

.item-carrinho .info-livro {
  display: flex;
  margin-bottom: 10px;
  color: white;
}
.detalhes-livro {
  display: flex;
  flex-direction: column;
  width: 100%;
  font-family: 'Mukta', sans-serif;
}
.detalhes-livro p {
  margin: 0;
}
.detalhes-livro div {
  display: flex;
  justify-content: space-between;
  width: 100%;
}

.detalhes-livro input[type='number'] {
  width: 50px;
  text-align: center;
  border: none;
  border-bottom: 1px solid rgb(2, 88, 88);
  background-color: transparent;
  margin-left: 10px;
  color: white;
}

.detalhes-livro button {
  background-color: transparent;
  border: none;
  cursor: pointer;
  font-size: 1.5rem;
  color: rgb(2, 88, 88);
  padding: 0;
  margin: 0;
}

.info-livro-preco {
  margin-left: auto;
}
.icon-capa-livro {
  width: 30px;
  margin-right: 10px;
}
</style>
