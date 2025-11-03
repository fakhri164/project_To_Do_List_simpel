<template>
    <div class="space-y-3 px-4">
        <TodoItem
            v-for="todo in todos"
            :key="todo.id"
            :todo="todo"
            @delete="$emit('delete', todo.id)"
            @save="$emit('save', todo.id, $event)"
        />
    </div>
</template>

<script setup>
import TodoItem from './TodoItem.vue';
defineProps({
    todos: Array,
})


const emit = defineEmits('delete', 'edit', 'save')

</script>