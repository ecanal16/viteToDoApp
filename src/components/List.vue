<script setup>
import useTodos from '../composables/useTodos';

const { pending, completed, changeStatus } = useTodos();

defineProps({
  isCompleted: {
    default: false,
    type: Boolean,
  },
});

</script>

<template>
    <div class="w-1/3">
  <h3 class="text-2xl text-center" :class="isCompleted ? 'text-red-600' : 'text-amber-400'">{{ isCompleted ? "Completed" : "Pending" }}</h3>
  <ul class="pt-8 space-y-4">
    <li v-for="todo in isCompleted ? completed : pending" :key="todo.id" @click="changeStatus(todo.id)" :class="isCompleted ? 'text-red-300 hover:bg-red-400' : 'text-amber-200 hover:bg-amber-400'" class="bg-gray-300 w-full text-center px-4 py-2 rounded-lg font-bold hover:cursor-pointer hover:text-cyan-700 duration-500">{{ todo.text}}</li>
  </ul>
</div>
</template>