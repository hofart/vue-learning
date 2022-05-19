<script setup>
import { setup } from '../components/Form.vue';

console.log(setup)
</script>

<template>
  <h1 class="underline">TodoList</h1>
  <ul>
    <li v-for="todo in todos" :key="todo.id">
      {{todo.title}}
    </li>
  </ul>
</template>