<script setup>
import { ref } from 'vue';

const newTitle = ref('');
const newContent = ref('');
const todos = ref([]);

function addNewTodo() {
  if (!newTitle.value.trim()) {
    return false;
  }

  todos.value.push({
    id: parseInt(Math.random() * 9999),
    title: newTitle.value,
    description: newContent.value,
    isChecked: false
  })

  newTitle.value = ''
  newContent.value = ''

  return true;
}
</script>

<template>
  <div>
    <form @submit.prevent="addNewTodo">
      <input v-model="newTitle" type="text" name="title" placeholder="Title">
      <textarea  v-model="newContent" name="description" placeholder="Description"></textarea>
      <button>Add new todo</button>
    </form>
    
    <ul>
      <li v-for="todo in todos" :key="todo.id">
        {{todo.title}}
      </li>
    </ul>
  </div>
</template>