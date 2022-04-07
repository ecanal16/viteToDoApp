<script setup>

import Title from "./components/Title.vue";
import List from "./components/List.vue";

</script>

<template>
<div class="min-h-screen bg-blue-400">
<div class="container mx-auto flex flex-col space-y-8 pt-8">
 <Title />
 
 <div class="flex justify-around"> 
<List />
<List isCompleted />
</div>
 </div>
</div>
</template>

