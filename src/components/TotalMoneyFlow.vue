<script setup>
import { defineProps, computed , ref, reactive, onMounted, watch} from 'vue';

const myObj = reactive({
  name: 'John',
  age: 30,
  children: {
    name: 'Jane',
    age: 2
  }
})


const props= defineProps({
  totalAmount: {
    type:Number,
    required:true
  },
  totalIncome: {
    type:Number,
    required:true
  },
  totalExpense: {
    type:Number,
    required:true}
})
function handleClick() {
  myObj.children.name = 'Doe'
}

watch( () => myObj.children.name, ()=> {
  console.log('Name changed')
}, )

</script>

<template>
  <div class="total-money-flow">
    <h1> Your Balance : {{ totalAmount }}</h1>
    <div class="income-expense">
      <h2 class="income">Income : {{ totalIncome }}</h2>
      <h2 class="expense">Expense : {{ totalExpense }}</h2>
    </div>

    <div class="random">
      <h2>Ranodm experiment with Reactive   name is {{ myObj.children.name }} </h2>
      <button @click="handleClick">Change Name</button>
    </div>
  </div>

</template>

<style scoped>
  
  .income-expense {
    display: flex;
    justify-content: space-around;
  }
</style>