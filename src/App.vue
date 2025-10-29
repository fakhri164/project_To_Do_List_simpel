<script setup>
import {ref, reactive} from 'vue' ;
import BaseInput from './components/Base/BaseInput.vue';
import BaseButton from './components/Base/BaseButton.vue';
import TodoList from './components/Todo/TodoList.vue';

const newTodo= ref()
const todos = reactive([])

let nextId =1

const handleAdd = () => {
  if(newTodo.value.trim()){
    todos.push({
      id: nextId++,
      text: newTodo.value,
      completed: false
    })

    newTodo.value = ''
  }
}

const handleDelete =(id) => {
  const index = todos.findIndex(todo => todo.id === id)
  if(index > -1) todos.splice(index, 1)
}




</script>

<template>
  <div class="min-h-screen bg-gradient-to-br from-teal-700 to-purple-700 p-4 sm:p-6 lg:p-8">
    <div class=" max-w-sm sm:max-w-md lg:max-w-2xl mx-auto my-10">
      <h1 class="text-xl lg:text-5xl text-white font-bold text-center mb-5 mt-1.5">MY TO DO LIST</h1>
    
      <div class="flex gap-3 px-4 mb-6">
      <BaseInput 
        v-model="newTodo"
        id="add-input"
        placeholder="Masukan to do list"
        type="text"
        @enter="handleAdd"
      />
      
      <BaseButton 
        label="Add To Do"
        variant="primary"
        @click="handleAdd"
      />
    </div>

    <div>
      <TodoList
        :todos="todos"
        @delete="handleDelete"
      />
    </div>
    </div>
  </div>
</template>


