<template>
  <Header />
  <Balance :totalBalance="total" />
  <!-- plus is added to make them numbers, since bydefault they becam strings -->
  <IncomeExpense :income="+income" :expenses="+expenses" />
  <TransactionList :transactions="transactions" @transactionDeleted="handleTransactionDeleted" />
  <AddTransaction @transactionSubmitted="handleTransactionSubmitted" />
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

onMounted(() => {
const saveTransactions  = JSON.parse(localStorage.getItem('transactions'))

if(saveTransactions){
  transactions.value = saveTransactions
}
})

const transactions = ref([
  { id: 1, text: "Your First Transaction", amount: 1000 },

]);

// Get Total
const total = computed(() => {
  return transactions.value.reduce((acc, item) => (acc += item.amount), 0);
});

//Get Income
const income = computed(() => {
  return transactions.value
  .filter((item) => item.amount > 0)
  .reduce((acc, item) => (acc += item.amount), 0)
  .toFixed(2);
});

//Get Expenses
const expenses = computed(() => {
  return transactions.value
  .filter((item) => item.amount < 0)
  .reduce((acc, item) => (acc += item.amount), 0)
  .toFixed(2);
});

// Add transaction 👍
const handleTransactionSubmitted = (transactionData) => {
  transactions.value.push({
    id: Date.now(), // Generates a unique timestamp-based id
    text: transactionData.text,
    amount: transactionData.amount,
  });
  toast.success('Transaction added successfully')

  saveTransactionsToLocalStorage()
}

//Delete transaction
const handleTransactionDeleted = (id) => {
  console.log(id)
  transactions.value = transactions.value.filter(transaction => transaction.id !== id);
  toast('Transaction deleted successfully')

  saveTransactionsToLocalStorage()
}

//Saving to local storage ✊
const saveTransactionsToLocalStorage = () => {
  localStorage.setItem('transactions', JSON.stringify(transactions.value))
}
</script>
