<template>
  <Header />
  <div class="container">
    <Balance :total="+total" />
    <IncomeExpense :income="income" :expense="+expense" />
    <TransactionList :arry="arry" />
    <AddTransaction />
  </div>
</template>

<script setup>
import Header from "./components/Header.vue";
import Balance from "./components/Balance.vue";
import IncomeExpense from "./components/IncomeExpense.vue";
import TransactionList from "./components/TransactionList.vue";
import AddTransaction from "./components/AddTransaction.vue";
import { ref, computed } from "vue";

var arry = ref([
  { id: 1, text: "icnome", amount: 490 },
  { id: 2, text: "expense", amount: -200 },
  { id: 2, text: "pipi lalala", amount: -20 },
]);
// total

const total = computed(() => {
  return arry.value.reduce((jug, item) => {
    return jug + item.amount;
  }, 0);
});
// icnome
const income = computed(() => {
  return arry.value
    .filter((transaction) => transaction.amount > 0)
    .reduce((jug, transaction) => jug + transaction.amount, 0)
    .toFixed(2);
});
// Get income
// const income = computed(() => {
//   return arry.value
//     .filter((transaction) => transaction.amount > 0)
//     .reduce((acc, transaction) => acc + transaction.amount, 0)
//     .toFixed(2);
// });
// expense
const expense = computed(() => {
  return arry.value
    .filter((item) => item.amount < 0)
    .reduce((jug, nextVal) => jug + nextVal.amount, 0);
});
</script>
