<template>
  <div class="container">
    <Header
      @add-task="showAddTask = !showAddTask"
      title="Task Tracker"
      :showAddTask="showAddTask"
    ></Header>
    <AddTask v-if="showAddTask" @new-task="onAddTask"></AddTask>
    <Tasks
      @toggle-reminder="toggleReminder"
      @delete-task="deleteTask"
      :tasks="tasks"
    ></Tasks>
  </div>
</template>

<script>
  import Header from "./components/Header.vue";
  import Tasks from "./components/Tasks.vue";
  import AddTask from "./components/AddTask.vue";
  export default {
    name: "App",
    components: { Header, Tasks, AddTask },
    data() {
      return {
        tasks: [],
        showAddTask: false,
      };
    },
    methods: {
      deleteTask(id) {
        if (confirm("Are you sure ?")) {
          this.tasks = this.tasks.filter((task) => task.id !== id);
        }
      },
      toggleReminder(id) {
        let task = this.tasks.find((t) => t.id === id);
        task.reminder = !task.reminder;
      },
      onAddTask(task) {
        this.tasks = [...this.tasks, task];
      },
    },
    created() {
      this.tasks = [
        {
          id: 1,
          text: "Bring groccery",
          time: "October 7 at 10pm",
          reminder: true,
        },
        {
          id: 2,
          text: "Attend Interview",
          time: "October 8 at 1pm",
          reminder: "False",
        },
        {
          id: 3,
          text: "Buy Sweets",
          time: "October 10 at 7pm",
          reminder: false,
        },
      ];
    },
  };
</script>

<style>
  @import url("https://fonts.googleapis.com/css2?family=Poppins:wght@300;400&display=swap");
  * {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
  }
  body {
    font-family: "Poppins", sans-serif;
  }
  .container {
    max-width: 500px;
    margin: 30px auto;
    overflow: auto;
    min-height: 300px;
    border: 1px solid steelblue;
    padding: 30px;
    border-radius: 5px;
  }
  .btn {
    display: inline-block;
    background: #000;
    color: #fff;
    border: none;
    padding: 10px 20px;
    margin: 5px;
    border-radius: 5px;
    cursor: pointer;
    text-decoration: none;
    font-size: 15px;
    font-family: inherit;
  }
  .btn:focus {
    outline: none;
  }
  .btn:active {
    transform: scale(0.98);
  }
  .btn-block {
    display: block;
    width: 100%;
  }
</style>
