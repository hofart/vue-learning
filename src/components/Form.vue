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
  <main class="w-[650px] max-w-full mx-auto py-24">
    <form class="flex gap-4 flex-col" @submit.prevent="addNewTodo">
      <input class="bg-transparent" v-model="newTitle" type="text" name="title" placeholder="Title">
      <textarea class="bg-transparent" v-model="newContent" name="description" placeholder="Description"></textarea>
      <button class="bg-red-700 text-white py-2 px-4">Add new todo</button>
    </form>
  </main>

  <ul>
    <li v-for="todo in todos" :key="todo.id">
      {{todo.title}}
    </li>
  </ul>
</template>