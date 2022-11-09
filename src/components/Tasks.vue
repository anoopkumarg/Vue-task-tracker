<template>
  <div :key="task.id" v-for="task in tasks">
    <Task
      @dblclick="$emit('toggle-reminder', task.id)"
      @delete-task="$emit('delete-task', task.id)"
      :task="task"
    ></Task>
  </div>
</template>

<script>
  import Task from "./Task.vue";
  export default {
    name: "Tasks",
    components: { Task },
    props: {
      tasks: Array,
    },
    emits: ["delete-task", "toggle-reminder"],
  };
</script>
<style scoped>
  div {
    margin: 10px auto;
  }
</style>
