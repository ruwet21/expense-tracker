<template>
  <div class="space-y-4 mb-6">
    <h3 class="text-slate-900 font-semibold px-1">Transactions</h3>

    <div class="space-y-3">
      <div
        v-for="transaction in transactions"
        :key="transaction.id"
        class="bg-white rounded-lg shadow-sm p-4 flex justify-between items-center border border-slate-100"
      >
        <span class="text-slate-700">
          {{ transaction.text }}
        </span>

        <span
          :class="
            transaction.amount < 50
              ? 'text-red-500 font-semibold'
              : 'text-green-500 font-semibold'
          "
        >
          ${{ transaction.amount }}
        </span>
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
