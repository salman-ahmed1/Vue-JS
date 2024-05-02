<template>
    <h3>Add Transaction</h3>
    <form id="form">
        <div class="form-control">
            <label for="tect">Text</label>
            <input type="text" id="text" placeholder="Enter Text..">
        </div>
        <div class="form-control">
            <label for="amount">
            >Amount <br>
            (negatuve - expense, positive + income)
            </label> 
            <input type="number" placeholder="Enter Amount..."  id ="amount">
            
        </div>
        <button class="btn">Add Transaction</button>
    </form>
</template>