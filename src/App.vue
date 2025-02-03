<template>
  <Header />
  <Balance :totalBalance="total" />
  <!-- plus is added to make them numbers, since bydefault they becam strings -->
  <IncomeExpense :income="+income" :expenses="+expenses" />
  <TransactionList :transactions="transactions" />
  <AddTransaction @transactionSubmitted="handleTransactionSubmitted" />
</template>

<script setup>
import Header from "./components/Header.vue";
import Balance from "./components/Balance.vue";
import IncomeExpense from "./components/IncomeExpense.vue";
import TransactionList from "./components/TransactionList.vue";
import AddTransaction from "./components/AddTransaction.vue";

import { ref, computed } from "vue";
import { useToast } from "vue-toastification";

const toast = useToast()

const transactions = ref([
  { id: 1, text: "Flower", amount: -120 },
  { id: 2, text: "Salary", amount: 800000 },
  { id: 3, text: "Book", amount: -1100 },
  { id: 4, text: "Camera", amount: 15000 },
]);
// console.log("Transct",transactions.value)

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
const handleTransactionSubmitted = (transactionData) => {
  transactions.value.push({
    id: Date.now(), // Generates a unique timestamp-based id
    text: transactionData.text,
    amount: transactionData.amount,
  });
  toast.success('Transaction added successfully')
}

</script>
