<template>
  <div class="flex flex-col gap-2">
    <TodoForm @add-todo="addTodo" />
    <TodoList :filteredTodos="filteredTodos" @remove-todo="removeTodo" />
    <button
      class="px-3 py-1 bg-emerald-500 text-white rounded-md"
      @click="toggleHideCompleted"
    >
      {{ hideCompleted ? "Show all" : "Hide completed" }}
    </button>
  </div>
</template>

<script setup>
import { ref, computed } from "vue";
import TodoForm from "./TodoForm.vue";
import TodoList from "./TodoList.vue";

const todos = ref([
  { id: 0, text: "Learn HTML", done: true },
  { id: 1, text: "Learn JavaScript", done: true },
  { id: 2, text: "Learn Vue", done: false }
]);

const hideCompleted = ref(false);

const filteredTodos = computed(() => {
  return hideCompleted.value ? todos.value.filter((t) => !t.done) : todos.value;
});

function addTodo(todo) {
  todos.value.push(todo);
}

function removeTodo(todo) {
  todos.value = todos.value.filter((t) => t !== todo);
}

function toggleHideCompleted() {
  hideCompleted.value = !hideCompleted.value;
}
</script>
