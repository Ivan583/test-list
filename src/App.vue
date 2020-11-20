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
      tasks: [
        {
          id: 1,
          title: "продукты",
          description: "купить хлеб",
          stage: "pending"
        },
        {
          id: 2,
          title: "животные",
          description: "накормить кота",
          stage: "completed"
        },
        {
          id: 3,
          title: "деловая",
          description: "написать проект",
          stage: "in work"
        }
      ]
    };
  },

  methods: {
    addTask(elem) {
      console.log(elem);
    }
  },

  created() {
    bus.$on("remove-task", data => {
      const id = data;
      this.tasks = this.tasks.filter(t => t.id !== id);
    });
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
