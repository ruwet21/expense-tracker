<template>
  <div class="space-y-4">
    <h3 class="text-slate-900 font-semibold px-1">Transactions</h3>

    <div class="space-y-3">
      <!-- contoh 1 item -->
      <div
        v-for="transaction in transactions"
        :key="transaction.id"
        class="card p-4 flex justify-between items-center"
        
      >
        {{ transaction.text }} <span :class="transaction.amount < 50 ? 'text-red-500' : 'text-green-500'"">${{ transaction.amount }}</span>
      </div>

      <p
        v-if="transactions.length === 0"
        class="text-slate-400 text-sm text-center py-4"
      >
        No transactions yet.
      </p>
    </div>
  </div>
</template>
<script setup>
import { defineProps } from "vue";

const props = defineProps({
  transactions: {
    type: Array,
    required: true,
  },
});
</script>
