<template>
  <div class="bg-white rounded-xl shadow-md p-8 text-center mb-6">
    <p class="text-slate-500 text-sm mb-1">Total Balance</p>
    <h2 class="text-4xl font-bold text-slate-900">${{ total }}</h2>
  </div>
</template>

<script setup>
import { defineProps } from "vue";

const props = defineProps({
  total: {
    type: Number,
    required: true,
  },
});
</script>
