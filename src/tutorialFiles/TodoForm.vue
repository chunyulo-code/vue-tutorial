<template>
  <form @submit.prevent="addTodo">
    <input v-model="newTodo" class="border border-gray-800 rounded-lg px-2" />
    <button class="ml-3 px-3 py-1 bg-emerald-500 text-white rounded-full">
      Add Todo
    </button>
  </form>
</template>

<script setup>
import { ref } from "vue";
const emit = defineEmits(["add-todo"]);

const newTodo = ref("");
const id = ref(0);

const addTodo = () => {
  emit("add-todo", { id: id.value++, text: newTodo.value, done: false });
  newTodo.value = "";
};
</script>
