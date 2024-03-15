<template>
  <div class="history">
    <ul>
     <li v-for="trasaction in transactions" :key="trasaction.id" >
      {{ trasaction.text }} <span>{{ trasaction.amount }}</span>
      <button @click="emit('delete-transactions', trasaction.id)" class="delete-btn">x</button>
     </li>
    </ul>
  </div>
</template>

<script setup>

import { defineProps ,defineEmits } from 'vue';

const props = defineProps({
  transactions: {
    type:Array,
    required:true
  }
})

const emit = defineEmits(['delete-transactions'])

console.log(props.transactions)

</script>
