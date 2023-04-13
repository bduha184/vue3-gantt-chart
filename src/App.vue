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
        <div class="base" v-show="show">
          <div class="overlay" v-show="show" @click="show = false"></div>
          <div class="content" v-show="show">
            <h2 class="font-bold">タスクの追加</h2>
            <div class="my-4">
              <label class="text-xs">カテゴリーID:</label>
              <select
                v-model="form.category_id"
                class="text-xs border px-4 py-2 rounded-lg"
              >
                <option
                  v-for="category in categories"
                  :key="category.id"
                  :value="category.id"
                >
                  {{ category.name }}
                </option>
              </select>
            </div>
            <div class="my-4">
              <label class="text-xs">ID:</label>
              <input
                class="text-xs border rounded-lg px-4 py-2"
                v-model.number="form.id"
              />
            </div>
            <div class="my-4">
              <label class="text-xs">タスク名:</label>
              <input
                class="text-xs border rounded-lg px-4 py-2"
                v-model="form.name"
              />
            </div>
            <div class="my-4">
              <label class="text-xs">担当者:</label>
              <input
                class="text-xs border rounded-lg px-4 py-2"
                v-model="form.incharge_user"
              />
            </div>
            <div class="my-4">
              <label class="text-xs">開始日:</label>
              <input
                class="text-xs border rounded-lg px-4 py-2"
                v-model="form.start_date"
                type="date"
              />
            </div>
            <div class="my-4">
              <label class="text-xs">完了期限日:</label>
              <input
                class="text-xs border rounded-lg px-4 py-2"
                v-model="form.end_date"
                type="date"
              />
            </div>
            <div class="my-4">
              <label class="text-xs">進捗度:</label>
              <input
                class="text-xs border rounded-lg px-4 py-2"
                v-model="form.percentage"
                type="number"
              />
            </div>
            <div>
              <button
                class="bg-indigo-500 hover:bg-indigo-700 text-white font-bold py-2 px-4 rounded-lg flex items-center"
                @click="saveTask"
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
            </div>
          </div>
        </div>
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
      form: {
        category_id:'',
        id: "",
        name: "",
        start_date: "",
        end_date: "",
        incharge_user: "",
        percentage: 0,
      },
    };
  },
  methods: {
    addTask() {
      this.show = true;
    },
    saveTask(){
      this.tasks.push(this.form);
      this.form = {};
      this.show = false
    }
  },
  mounted() {
    this.addTask();
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
