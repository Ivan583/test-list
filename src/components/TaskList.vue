<template>
  <ul>
    <TaskItem v-for="(item, index) in items" :key="item.id" :elem="item" :index="index" />
  </ul>
</template>

<script>
import TaskItem from "@/components/TaskItem.vue";
export default {
  props: ["items"],
  components: { TaskItem }
};
</script>

<style scoped>
ul {
  list-style-type: none;
  padding: 0;
  margin: 0;
}
</style>
