<template>
  <ul>
    {{ items }}
    <TaskItem />
  </ul>
</template>

<script>
import TaskItem from "@/components/TaskItem.vue";
export default {
  props: ["items"],
  components: { TaskItem }
};
</script>
