<template>
  <AddTask @click="addTask"/>
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
              v-for="category in category_data"
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
</template>

<script>
import AddTask from './AddTask.vue';
import category_data from "../data/categories.json";
import task_data from "../data/tasks.json";

export default {
  components:{
    AddTask,
  },
  data() {
    return {
      show:false,
      category_data,
      task_data,
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
      this.task_data.push(this.form);
      this.form = {};
      this.show = false
    }
  },
  mounted() {
    this.saveTask();
  },
};
</script>
