<script setup>

import {ref, defineProps, defineEmits} from 'vue';

const props = defineProps({
  transactions:Array
})

const emit = defineEmits(['add-transaction'])
const inputTText = ref('')
const inputAmount = ref('')


function handleAddTransaction() {


const newTransaction = {
  text: inputTText.value,
  amount: inputAmount.value
}

emit('add-transaction', newTransaction)
inputAmount.value = ''
inputTText.value= ''

}

</script>


<template>
  <div class="add-transaction">

    <h3>Add Transaction</h3>
    <form @submit.prevent="handleAddTransaction">
      <div class="form-control">
        <div>
          <label for="text">Text : </label>
          <input type="text" class="text" placeholder="Enter text..." v-model="inputTText" />
        </div>
        <div>
          <label for="amount">Amount: </label>
          <input type="number" class="amount" placeholder="Enter amount..."  v-model="inputAmount"/>
        </div>
        <button class="btn">Add Transaction</button>
      </div>
    </form>
  </div>
</template>

