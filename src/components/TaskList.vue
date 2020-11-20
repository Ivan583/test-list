<template>
  <ul>
    <TaskItem v-for="item in items" :key="item.id" :elem="item" @remove-task="removeTask" />
  </ul>
</template>

<script>
import TaskItem from "@/components/TaskItem.vue";
export default {
  props: ["items"],
  components: { TaskItem },
  methods: {
    removeTask(id) {
      this.$emit("remove-task", id);
    }
  }
};
</script>

<style scoped>
ul {
  list-style-type: none;
  padding: 0;
  margin: 0;
}
</style>
