<script setup lang="ts">
import Item, {itemType} from './components/Item.vue'
import { reactive } from 'vue'

type store = {
  items: itemType[]
}

const store = reactive<store>({
  items: []
})

fetch('http://localhost:3000/items')
    .then(response => response.json())
    .then(data => {
      store.items = [...data]}
      );

</script>

<template>
  <ul>
    <Item v-for="itemVal in store.items" :key="itemVal.id" :id="itemVal.id" :text="itemVal.text" :checked="itemVal.checked"/>
  </ul>
    
</template>

<style scoped>

.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
  transition: filter 300ms;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
</style>
