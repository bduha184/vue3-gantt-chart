<script setup>
import Task from "./components/Task.vue";
import Carendar from "./components/Carendar.vue";
</script>

<template>
  <div class="wrapper">
    <div id="gantt-header" class="h-12 p-2 flex items-center">
      <h1 class="text-xl font-bold">ガントチャート</h1>
    </div>
    <div id="gantt-content" class="flex">
      <Task />
      <Carendar />
    </div>
  </div>
</template>

<style scoped></style>
