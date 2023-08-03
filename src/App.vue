<script setup>
import TodoApp from "./components/TodoApp.vue";
</script>

<template>
  <div
    class="w-screen h-screen flex flex-col justify-center items-center gap-6"
  >
    <header class="text-[40px] font-black">TODO LIST</header>
    <main>
      <TodoApp />
    </main>
  </div>
</template>
