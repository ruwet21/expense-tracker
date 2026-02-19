<template>
  <div class="card p-8 text-center">
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
