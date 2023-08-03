<template>
  <ul class="flex flex-col gap-2">
    <li
      v-for="todo in filteredTodos"
      :key="filteredTodos.id"
      class="flex gap-2"
    >
      <input type="checkbox" v-model="todo.done" />
      <span :class="{ [`line-through`]: todo.done }" class="text-lg">{{
        todo.text
      }}</span>
      <button
        class="px-1 rounded-sm bg-red-400 text-white"
        @click="removeTodo(todo)"
      >
        X
      </button>
    </li>
  </ul>
</template>

<script setup>
import { defineProps, defineEmits } from "vue";

const { filteredTodos, hideCompleted } = defineProps([
  "filteredTodos",
  "hideCompleted"
]);

const emit = defineEmits(["remove-todo"]);

const removeTodo = (todo) => {
  emit("remove-todo", todo);
};
</script>
