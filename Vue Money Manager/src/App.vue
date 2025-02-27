<template>
  <Header />
  <div class="container">
    <Balance :total="+total" />
    <IncomeExpense :income="+income" :expense="+expense" />
    <TransactionList :arry="arry" @dltIdEvent="dltTransaction" />
    <AddTransaction @transactionSubmitted="onTransactionSubmit" />
  </div>
</template>

<script setup>
import Header from "./components/Header.vue";
import Balance from "./components/Balance.vue";
import IncomeExpense from "./components/IncomeExpense.vue";
import TransactionList from "./components/TransactionList.vue";
import AddTransaction from "./components/AddTransaction.vue";
import { ref, computed, onMounted } from "vue";
import { useToast } from "vue-toastification";
const toast = useToast()
var arry = ref([

]);
// load transacion from storage
onMounted(() => {
  const savedTrans = JSON.parse(localStorage.getItem('transactionData'))
  if (savedTrans) {
    arry.value = savedTrans
  }
})

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

// add tranaction
const onTransactionSubmit = (fulusData) => {
  arry.value.length == 0 ? (fulusData.id = 1) : (fulusData.id = arry.value.at(-1).id + 1);
  console.log(fulusData.id)
  arry.value.push({ ...fulusData })
  onChange()
  toast.success("Success " + (fulusData.amount > 0 && "+" || '') + fulusData.amount + " $")
}

// delit transaction
const dltTransaction = (id) => {
  console.log(id)
  arry.value = arry.value.filter((items) => items.id !== id)
  onChange()
  toast.success('Deleted entry Sucessfully')
}

// save to local storage
const onChange = () => {
  localStorage.setItem('transactionData', JSON.stringify(arry.value))
}

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
