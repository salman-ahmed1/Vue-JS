<template>
    <h3>Add Transaction</h3>
    <form id="form" @submit.prevent="onSubmit">
        <div class="form-control">
            <label for="text">Text</label>
            <input type="text" id="text" v-model="text" placeholder="Enter Text..">
        </div>
        <div class="form-control">
            <label for="amount">
            >Amount <br>
            (negatuve - expense, positive + income)
            </label> 
            <input type="text" v-model="amount" placeholder="Enter Amount..." id="amount">
            
        </div>
        <button class="btn">Add Transaction</button>
    </form>
</template>
<script setup>

import {ref} from "vue"
import { useToast } from "vue-toastification";
const text=ref("")
const amount=ref("")
const toast=useToast()
const emit=defineEmits('transactionSubmitted')
const onSubmit = () => {
    if (!text.value || !amount.value) {
        toast.error("Both fields must be filled")
    } else {
        
        const transactionData={
        text:text.value,
        amount:parseFloat(amount.value)
    } 
    emit("transactionSubmitted",transactionData)
    
   text.value=""
   amount.value=""
}
}

</script>