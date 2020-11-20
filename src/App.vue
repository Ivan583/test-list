<template>
  <div id="app">
    <h1>Список задач</h1>
    <AddTask @add-task="addTask" />
    <hr />
    <TaskList :items="tasks" />
  </div>
</template>

<script>
import { bus } from "@/bus.js";
import TaskList from "@/components/TaskList.vue";
import AddTask from "@/components/AddTask.vue";

export default {
  name: "App",
  components: { TaskList, AddTask },
  data() {
    return {
      tasks: []
    };
  },

  methods: {
    addTask(elem) {
      this.tasks.push(elem);
      localStorage.setItem("tasks", JSON.stringify(this.tasks));
    }
  },

  created() {
    bus.$on("remove-task", data => {
      const id = data;
      this.tasks = this.tasks.filter(t => t.id !== id);
      localStorage.setItem("tasks", JSON.stringify(this.tasks));
    });
  },

  mounted() {
    try {
      const data = localStorage.getItem("tasks");
      data ? (this.tasks = JSON.parse(data)) : null;
    } catch {
      if (err == QUOTA_EXCEEDED_ERR) {
        alert("quota exceeded");
      }
    }
  }
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  font-size: 1.2rem;
  color: blue;
  margin-top: 40px;
}
</style>
