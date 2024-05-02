<template>
 <Header /> 
  <div class="container"> 
    <Balance />
    <IncomeExpenses /> 
    <TransactionList :arry="arry" />
    <AddTransaction />
  </div>
</template>



<script setup>
import Header from "./components/Header.vue";
import Balance from "./components/Balance.vue";
import IncomeExpenses from "./components/IncomeExpense.vue";
import TransactionList from "./components/TransactionList.vue";
import AddTransaction from "./components/AddTransaction.vue";


var arry = [
            {id:1,text:"icnome",amount:490},
            {id:2,text:"expense",amount:-200},
            {id:2,text:"pipi lalala",amount:-20},]
</script>