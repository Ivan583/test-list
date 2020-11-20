<template>
  <ul>
    <TaskItem v-for="item in items" :key="item.id" :elem="item" />
  </ul>
</template>

<script>
import TaskItem from "@/components/TaskItem.vue";
export default {
  props: ["items"],
  components: { TaskItem }
};
</script>
