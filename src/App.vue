<template>
  <div class="wrapper">
    <div id="gantt-header" class="h-12 p-2 flex items-center">
      <h1 class="text-xl font-bold">ガントチャート</h1>
      <TaskForm />
    </div>
    <div id="gantt-content" class="flex">
      <Carendar />
    </div>
  </div>
</template>

<script>
import category_data from './data/categories.json';
import task_data from './data/tasks.json';
import Carendar from "./components/Carendar.vue";
import TaskForm from "./components/TaskForm.vue";

export default {
  name: "App",
  components: {
    Carendar,
    TaskForm,
  },
  data() {
    return {
      category_data,
      task_data,
    };
  },
  methods: {

  },
  mounted() {
  },
};
</script>

<style>
.base {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  display: flex;
  justify-content: center;
  margin-top: 50px;
}

.overlay {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background-color: gray;
  opacity: 0.5;
}

.content {
  background-color: white;
  position: relative;
  border-radius: 10px;
  padding: 40px;
}
</style>
