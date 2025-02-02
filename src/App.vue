<script>
import Header from './components/Header.vue';
import Balance from './components/Balance.vue';
import IncomeExpense from './components/IncomeExpense.vue';
import TransationList from './components/TransationList.vue';
export default {
  components: {
    Header,
    Balance,
    IncomeExpense,
    TransationList,
  }
}
</script>

<template>
<!-- My App -->
<Header />
<Balance />
<IncomeExpense />
<TransationList />
</template>