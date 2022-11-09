<template>
  <div :class="[task.reminder ? 'reminder' : '', 'task']">
    <h3>
      {{ task.text }}
      <i class="fas fa-times" @click="onDelete(task.id)"></i>
    </h3>
    <p>{{ task.time }}</p>
  </div>
</template>

<script>
  export default {
    name: "Task",
    props: {
      task: Object,
    },
    methods: {
      onDelete(id) {
        this.$emit("delete-task", id);
      },
    },
  };
</script>

<style>
  .task {
    background: #f4f4f4;
    padding: 10px 20px;
    margin-bottom: 5px;
    cursor: pointer;
  }

  .fas {
    color: red;
    float: right;
  }

  .reminder {
    border-left: 5px solid green;
  }
</style>
