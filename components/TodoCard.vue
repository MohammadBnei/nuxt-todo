<template>
    <div class="max-w-sm rounded overflow-hidden shadow-lg mb-4">
        <div class="px-6 py-4">
            <div class="flex items-center justify-between">
                <label class="flex items-center cursor-pointer">
                    <input type="checkbox" v-model="isCompleted" @change="toggleComplete" class="mr-2" />
                    <span :class="{ 'line-through text-gray-500': isCompleted }">
                        {{ todo.text }}
                    </span>
                </label>
                <button @click="deleteTodo" class="text-red-500 hover:text-red-700">
                    Delete
                </button>
            </div>
        </div>
    </div>
</template>

<script setup lang="ts">
import { ref, defineProps, defineEmits } from 'vue';

interface Todo {
    id: number;
    text: string;
    completed: boolean;
}

// Define the props the component accepts
const props = defineProps<{
    todo: Todo;
}>();

// Define the events that can be emitted
const emit = defineEmits<{
    (e: 'toggle', id: number): void;
    (e: 'delete', id: number): void;
}>();

const isCompleted = ref(props.todo.completed);

// Emit the toggle event when checkbox state changes
const toggleComplete = () => {
    emit('toggle', props.todo.id); // Emit toggle event with the todo's id
};

// Emit the delete event when the delete button is clicked
const deleteTodo = () => {
    emit('delete', props.todo.id); // Emit delete event with the todo's id
};
</script>

<style scoped>

</style>