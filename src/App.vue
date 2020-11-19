<template>
  <div id="app">
    <h1>Список задач</h1>
    <hr />
    <TaskList :items="tasks" />
  </div>
</template>

<script>
import TaskList from "@/components/TaskList.vue";

export default {
  name: "App",
  components: { TaskList },
  data() {
    return {
      tasks: [
        { id: 1, title: "продукты", description: "купить хлеб" },
        { id: 2, title: "животные", description: "накормить кота" },
        { id: 3, title: "деловая", description: "написать проект" }
      ]
    };
  }
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
