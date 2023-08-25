<script setup>
import MeuCarrinho from '@/components/MeuCarrinho.vue'
import ListagemLivros from '@/components/ListagemLivros.vue'
</script>

<template>
  <h1>bolas da Copa do Mundo</h1>
  <div class="container-geral">
    <listagem-livros />
    <meu-carrinho />
  </div>
</template>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Bruno+Ace+SC&family=Press+Start+2P&display=swap');
.container-geral {
  /* display: flex;
  justify-content: space-between; */
  display: grid;
  grid-template-columns: 3fr 1fr;
}
h1 {
  font-family: 'Bruno Ace SC', cursive;
  text-align: center;
  padding: 5px;
  color: white;
  background-color: rgb(2, 88, 88);
  border-radius: 10px;
  border-color: rgb(255, 255, 255);
  border-style: groove;
  border-width: 7px;
}
</style>
