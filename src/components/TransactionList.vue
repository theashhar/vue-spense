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
      <!-- Cash <span>₹400</span> -->
      <button class="delete-btn">x</button>
    </li>
    <!-- 

        <li class="plus">
            Cash <span>₹800</span>
            <button class="delete-btn">x</button>
      </li> -->
  </ul>
</template>

<script setup>
  import {defineProps} from 'vue';

  const props = defineProps({
    transactions:{
      type: Array,
      required: true
    }
  });

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
