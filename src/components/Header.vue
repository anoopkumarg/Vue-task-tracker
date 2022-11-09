<template>
  <header>
    <h1>{{ title }}</h1>
    <Button
      @btn-click="$emit('add-task')"
      :text="showAddTask ? 'Close' : 'Add Task'"
      :colour="showAddTask ? 'red' : 'green'"
    ></Button>
  </header>
</template>

<script>
  import Button from "./Button.vue";
  export default {
    name: "Header",
    props: {
      title: String,
      showAddTask: Boolean,
    },
    components: {
      Button,
    },
    emits: ["add-task"],
  };
</script>

<style scoped>
  header {
    display: flex;
    justify-content: space-between;
    align-items: center;
  }
</style>
