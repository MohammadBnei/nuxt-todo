<template>
    <div class="container mx-auto mt-10">
        <h2 class="text-2xl font-bold mb-6">Todo List</h2>

        <!-- New Todo Form -->
        <NewTodoForm @add-todo="handleAddTodo" />

        <!-- Todo Items Display -->
        <transition-group name="fade">
            <TodoCard v-for="todo in todos" :key="todo.id" :todo="todo" @toggle="updateTodo" @delete="removeTodo" />
        </transition-group>
    </div>
</template>

<script setup lang="ts">

interface Todo {
    id: number;
    text: string;
    completed: boolean;
}

const todos = ref<Todo[]>([
    { id: 1, text: 'Task 1', completed: false },
    { id: 2, text: 'Task 2', completed: false },
    { id: 3, text: 'Task 3', completed: false },
]);

const handleAddTodo = (newTodo: Todo) => {
    todos.value.push({ ...newTodo, id: todos.value.length + 1 });
};

const updateTodo = (id: number) => {
    todos.value = todos.value.map((todo: Todo) => todo.id === id ? { ...todo, completed: !todo.completed } : todo);
};

const removeTodo = (id: number) => {
    todos.value = todos.value.filter((todo: Todo) => todo.id !== id);
};
</script>

<style scoped>
.fade-enter-active,
.fade-leave-active {
    transition: opacity 0.5s;
}

.fade-enter-from,
.fade-leave-to
/* .fade-leave-active dans <2.1.8 */
    {
    opacity: 0;
}
</style>