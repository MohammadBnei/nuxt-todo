<template>
  <div class="mb-4">
    <input v-model="todoText" type="text" placeholder="Add a new todo" class="border px-4 py-2 rounded w-full" />
    <button @click="addTodo" class="bg-blue-500 text-white px-4 py-2 rounded mt-2 hover:bg-blue-600">
      Add Todo
    </button>
  </div>
</template>

<script setup lang="ts">
const emit = defineEmits<{
  (e: 'add-todo', todo: { text: string; completed: boolean }): void;
}>();

const todoText = ref<string>('');

const addTodo = () => {
  if (todoText.value.trim()) {
    emit('add-todo', { text: todoText.value, completed: false });
    todoText.value = ''; // Reset the input field
  }
};
</script>

<style scoped>
/* You can add additional styles here if needed */
</style>