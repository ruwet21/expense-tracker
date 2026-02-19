<template>
  <div class="card p-6">
    <form @submit.prevent="onSubmit" class="space-y-4">
      <div>
        <label
          class="block text-xs font-medium text-slate-500 mb-1 uppercase tracking-wider"
        >
          Description
        </label>
        <input
          type="text"
          placeholder="e.g. Grocery"
          v-model="text"
          class="w-full px-4 py-3 bg-slate-50 border-none rounded-lg text-slate-900 placeholder:text-slate-400"
        />
      </div>

      <div>
        <label
          class="block text-xs font-medium text-slate-500 mb-1 uppercase tracking-wider"
        >
          Amount
        </label>
        <input
          type="number"
          step="0.01"
          placeholder="e.g. -45.00 or 100.00"
          v-model="amount"
          class="w-full px-4 py-3 bg-slate-50 border-none rounded-lg text-slate-900 placeholder:text-slate-400"
        />
      </div>

      <button
        type="submit"
        class="w-full bg-slate-900 text-white font-semibold py-4 rounded-lg"
      >
        Add Transaction
      </button>
    </form>
  </div>
</template>
<script setup>
import { useToast } from "vue-toastification";
import { ref } from "vue";

const text = ref("");
const amount = ref("");
// Get toast interface
const toast = useToast();

const emit = defineEmits(["add-transaction"]);
const onSubmit = () => {
  if (!text.value || !amount.value) {
    // Display a toast error message if either field is empty
    toast.error("Kolom harus diisi.");
    return;
  }

  const newTransaction = {
    id: Date.now(),
    text: text.value,
    amount: parseFloat(amount.value),
  };

  // Emit the new transaction to the parent component
  emit("add-transaction", newTransaction);

  // Clear the form
  text.value = "";
  amount.value = "";
};
</script>
