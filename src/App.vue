<script setup>
import { ref, computed } from "vue";

const newTodo = ref("");

const todos = ref([]);

const pending = computed(() => {
  return todos.value.filter((todo) => !todo.done);
});

const completed = computed(() => {
  return todos.value.filter((todo) => todo.done);
});

const addTodo = () => {
  if (newTodo.value.trim()) {
  todos.value.push({
    id: todos.value.length,
    content: newTodo.value,
    done: false,
  });
  newTodo.value = "";
  }
};


const changeStatus = (id) => {
  const todo = todos.value.find((todo) => todo.id === id);
  todo.done = !todo.done;
};
</script>

<template>
<div class="min-h-screen bg-slate-500">
<div class="container mx-auto flex flex-col space-y-8 pt-8">
 <h1 class="pb-4 font-thin text-center text-6xl tracking-tight text-cyan-200">🚀 ToDo App</h1>
 <input @change="addTodo" v-model="newTodo" type="text" class="rounded-lg text-center px-4 py-2 text-xl" placeholder="New Todo">
 <div class="flex justify-around"> 
<div class="w-1/3">
  <h3 class="text-2xl text-center text-amber-300">Pending</h3>
  <ul class="pt-8 space-y-4">
    <li v-for="todo in pending" :key="todo.id" @click="changeStatus(todo.id)" class="bg-gray-300 w-full text-center px-4 py-2 rounded-lg text-amber-200 font-bold hover:cursor-pointer hover:bg-amber-400 hover:text-cyan-700 duration-500">{{ todo. content}}</li>
  </ul>
</div>
<div class="w-1/3">
  <h3 class="text-2xl text-center text-red-300">Completed</h3>
  <ul class="pt-8 space-y-4">
    <li v-for="todo in completed" :key="todo.id" @click="changeStatus(todo.id)" class="bg-gray-300 w-full text-center px-4 py-2 rounded-lg text-red-300 font-bold hover:cursor-pointer hover:bg-red-400 hover:text-cyan-700 duration-500">{{ todo. content}}</li>
  </ul>
</div>
</div>
 </div>
</div>
</template>

