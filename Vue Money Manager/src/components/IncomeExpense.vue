<template>
 <div class="inc-exp-container">
    <div class="income">
        <h4>Income</h4>
            <p id=" money-plus" class="money plus">+${{ income }}</p>
    </div>
    <div class="expense">
        <h4>Expense</h4> 
        <p id=" money-minus" class="money minus">-${{-1*expense}}</p>
    </div>
       
</div>
</template>

<script setup>
// import { defineProps } from "vue";
const props = defineProps({
    income:{
        type:Number,
        required:true,
    },
    expense:{
        type:Number,
        required:true
    }
})

</script>