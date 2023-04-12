<template>
  <div class="wrapper">
    <div id="gantt-header" class="h-12 p-2 flex items-center">
      <h1 class="text-xl font-bold">ガントチャート</h1>
      <button
        class="bg-indigo-700 hover:bg-indigo-900 text-white py-2 px-4 rounded-lg flex items-center"
        @click="addTask"
      >
        <svg
          class="w-4"
          xmlns="http://www.w3.org/2000/svg"
          fill="none"
          viewBox="0 0 24 24"
          stroke="currentColor"
        >
          <path
            stroke-linecap="round"
            stroke-linejoin="round"
            stroke-width="2"
            d="M12 6v6m0 0v6m0-6h6m-6 0H6"
          />
        </svg>
        <span class="font-bold text-xs"> タスクを追加する </span>
      </button>
      <teleport to="#form">
        <div class="overlay" v-show="show" @click="show=false"></div>
      </teleport>
    </div>
    <div id="gantt-content" class="flex">
      <Carendar />
    </div>
  </div>
</template>

<script>
import Carendar from "./components/Carendar.vue";

export default {
  name: "App",
  components: {
    Carendar,
  },
  data() {
    return {
      show: false,
    };
  },
  methods: {
    addTask() {
      this.show = true;
    },
  },
  mounted() {
    this.addTask();
  },
};
</script>

<style>
.overlay {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background-color: gray;
  opacity: 0.5;
}

</style>
