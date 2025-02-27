<template>
<h3>History</h3>
<ul id="list" class="list">
  <li v-for="item in arry" :key="item.id" :class="item.amount<0?'minus':'plus' ">
    {{item.text}} <span >${{ item.amount }} </span> 
    <button @click="dltTransaction(item.id)" class="delete-btn">x</button>
</li>
    <!-- <li class="minus" >Cash <span >-$30 </span> 
        <button class="delete-btn">x</button>
    </li>
    <li class="plus" >Cash <span >+$300 </span> 
        <button class="delete-btn">x</button>
    </li> -->
</ul>
</template>

<script setup>

import { defineProps } from "vue";
const emit =defineEmits('dltIdEvent')
const props = defineProps({
    arry:{
        type:Array, 
        required:true,
    },
})
const dltTransaction=(id)=>{
    emit('dltIdEvent',id)
 
}
</script>

