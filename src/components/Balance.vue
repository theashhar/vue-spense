<template>
  <h4>Your Balance</h4>
  <h1 id="Balance">₹{{totalBalance}}</h1>
</template>

<script setup>
import { defineProps } from "vue";

const props = defineProps({
  totalBalance: {
    type: Number,
    required: true,
  },
});
</script>
