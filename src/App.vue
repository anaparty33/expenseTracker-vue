<script  setup >
import TotalMoneyFlow from './components/TotalMoneyFlow.vue';
import AddTransaction from './components/AddTransaction.vue';
import History from './components/History.vue';

import { ref , computed} from 'vue';
  const transactions = ref([
    { id: 1, text: 'Flower', amount: -20 },
    { id: 2, text: 'Salary', amount: 300 },
    { id: 3, text: 'Book', amount: -10 },
    { id: 4, text: 'Camera', amount: 150 }
  ])

const totalAmount = computed(() => {
  return transactions.value.reduce((acc, item) => (acc += item.amount), 0);
});

const totalExpense = computed(() => {
  return transactions.value
    .filter((item) => item.amount < 0)
    .reduce((acc, item) => (acc += item.amount), 0);
});

const totalIncome = computed(() => {
  return transactions.value
    .filter((item) => item.amount > 0)
    .reduce((acc, item) => (acc += item.amount), 0);
});


function onaddTransaction(newTransaction) {

  const updatedTransactionwithID =  {...newTransaction, id: transactions.value.length+1}
  transactions.value.push(updatedTransactionwithID)

}

function onDelelteTransaction(id) {
  transactions.value = transactions.value.filter((t => t.id !== id))
}

</script>

<template>
  <div class="expense-app-container">
    <total-money-flow  :totalAmount = "totalAmount" :totalIncome="totalIncome" :totalExpense="totalExpense"/>
    <history :transactions="transactions" @delete-transactions="onDelelteTransaction"/>
    <add-transaction  @add-transaction="onaddTransaction"/>
    
  </div>
</template>

