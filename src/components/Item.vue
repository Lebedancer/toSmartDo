<script setup lang="ts">
import { reactive } from 'vue'

export type itemType = {
  id: number,
  text: string,
  checked: boolean
}

const {id, text, checked} = defineProps<itemType>()
const store = reactive<Pick<itemType, 'checked'>>({checked})
function toggleDone() {
  store.checked = !store.checked
} 


</script>

<template>
  <li class="item" :class="store.checked ? 'done' : null">
    <button class="button" type="button" @click="toggleDone">
      <svg v-if="store.checked"  class="icon" fill="#000000" width="800px" height="800px" viewBox="0 0 24 24" id="d9090658-f907-4d85-8bc1-743b70378e93" data-name="Livello 1" xmlns="http://www.w3.org/2000/svg"><title>prime</title><path id="70fa6808-131f-4233-9c3a-fc089fd0c1c4" data-name="done circle" d="M12,0A12,12,0,1,0,24,12,12,12,0,0,0,12,0ZM11.52,17L6,12.79l1.83-2.37L11.14,13l4.51-5.08,2.24,2Z"/></svg>
      <div v-else class="cirlce icon"></div>
    </button>
    {{ text }}
  </li>
</template>

<style scoped>
.cirlce {
  border: 1px solid black;
  border-radius: 50%;
  box-sizing: border-box;
}

.item {
  margin: 5px 0;
  background: beige;
  list-style: none;
  padding: 5px 10px;
  border-radius: 5px;
  display: flex;
  align-items: center;
}

.item:first-child {
  margin-top: 0;
}

.done {
  background: rgb(98, 148, 98);
}

.button {
  margin: 0;
  padding: 0;
  background: none;
  border: none;
  outline: none;
}

.icon {
  width: 20px;
  height: 20px;
  margin-right: 10px;
}

</style>
