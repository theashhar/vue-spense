<template>
  <h3>History</h3>
  <ul id="list" class="list">
    <!-- to loop -->
    <li
      v-for="transaction in transactions"
      :key="transaction.id"
      :class="transaction.amount < 0 ? 'minus' : 'plus'"
    >
      {{ transaction.text }} <span>₹{{ transaction.amount }}</span>
      <button @click="deleteTransaction(transaction.id)" class="delete-btn">
        x
      </button>
    </li>
  </ul>
</template>

<script setup>
import {defineProps} from 'vue';

const emit = defineEmits(['transactionDeleted']);
const props = defineProps({
  transactions:{
    type: Array,
    required: true
  }
});

const deleteTransaction = (id) => {
  emit('transactionDeleted', id);
}
</script>

<!-- <script setup>
  //composition API
    const transactions = [
      { id: 1, text: "Flower", amount: -120 },
      { id: 2, text: "Salary", amount: 120000 },
      { id: 3, text: "Book", amount: -1100 },
      { id: 4, text: "Camera", amount: 15000 },
    ];

  // options API
  // data() {
  //   return {
  //     transactions: [
  //       { id: 1, text: "Flower", amount: -120 },
  //       { id: 2, text: "Salary", amount: 120000 },
  //       { id: 3, text: "Book", amount: -1100 },
  //       { id: 4, text: "Camera", amount: 15000 },
  //     ],
  //   };
  // },
</script> -->
