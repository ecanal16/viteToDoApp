<script setup>
import { ref } from "vue";
import useTodos from "../composables/useTodos";

const { addTodo } = useTodos();
const newTodo = ref("");

const add = () => {
  if (newTodo.value) {
    addTodo(newTodo.value);
    newTodo.value = "";
  }
};
</script>

<template>
    <h1 class="pb-4 font-thin text-center text-6xl tracking-tight text-cyan-200">📝 ToDo App using API</h1>
    <input @change="add" v-model="newTodo" type="text" class="rounded-lg text-center px-4 py-2 text-xl" placeholder="New Todo">
</template>