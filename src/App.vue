<template>
  <Header />
  <Balance :totalBalance="total" />
  <!-- plus is added to make them numbers, since bydefault they becam strings -->
  <IncomeExpense :income="+income" :expenses="+expenses" />
  <TransationList :transactions="transactions" />
  <AddTransaction />
</template>

<script setup>
import Header from "./components/Header.vue";
import Balance from "./components/Balance.vue";
import IncomeExpense from "./components/IncomeExpense.vue";
import TransationList from "./components/TransationList.vue";
import AddTransaction from "./components/AddTransaction.vue";

import { ref, computed } from "vue";

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
</script>
