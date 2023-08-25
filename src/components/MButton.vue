<script setup>
const props = defineProps ({ text: String})
</script>

<template>
<button>
  <slot>
   {{props.text}}
  </slot>
  </button>
</template>

<style scoped>
button {
  font-weight: bold;
  border-radius: 4px;
  color: white;
  background-color: rgb(2, 88, 88);
  padding: 5px 5px;
  margin: 10px 10px 10px 10px;
  cursor: pointer;
  font-family: 'Bruno Ace SC', cursive;
  border-color: rgb(255, 255, 255);
  border-style:groove;
  font-size: 15px;
  border-width: 2px;
}
</style>