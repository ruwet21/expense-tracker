<template>
  <div class="min-h-screen py-12 px-4 bg-slate-50">
    <div class="max-w-md mx-auto space-y-8">
      <HeaderTitle />
      <BalanceCard :total="total" />
      <Transactions :transactions="transactions" />
      <AddTransaction @add-transaction="handleTransactionSubmitted" />
    </div>
  </div>
</template>
<script setup>
import HeaderTitle from "./components/HeaderTitle.vue";
import BalanceCard from "./components/BalanceCard.vue";
import Transactions from "./components/Transactions.vue";
import AddTransaction from "./components/AddTransaction.vue";
import { ref, computed } from "vue";

const transactions = ref([]);
// Get total
const total = computed(() => {
  return transactions.value.reduce((acc, transaction) => {
    return acc + transaction.amount;
  }, 0);
});
// Generate unique ID
const generateUniqueId = () => {
  return Math.floor(Math.random() * 1000000);
};
// Submit transaction
const handleTransactionSubmitted = (newTransaction) => {
  transactions.value.push({
    id: generateUniqueId(),
    text: newTransaction.text,
    amount: newTransaction.amount,
  });
};
</script>
