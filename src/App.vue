<template>
  <div class="container">
    <Header
      title="Task Tracker"
      @add-task="addTask"
      :showAddTask="showAddTask"
      @toggle-task="toggleTask"
    />
    <Tasks @delete-task="deleteTask" @toggle-reminder="toggleReminder" :tasks="tasks" />
  </div>
</template>

<script>
import Header from './components/Header.vue';
import Tasks from './components/Tasks.vue';

export default {
  name: 'App',
  components: {
    Header,
    Tasks,
  },
  data() {
    return {
      tasks: [],
      showAddTask: false,
    };
  },
  methods: {
    deleteTask(id) {
      this.tasks = this.tasks.filter((task) => task.id !== id);
    },
    addTask(task) {
      this.tasks.push(task);
    },
    toggleTask() {
      this.showAddTask = !this.showAddTask;
    },
    toggleReminder(id) {
      this.tasks = this.tasks.filter((task) => {
        if (task.id === id) {
          this.task.reminder = !task.reminder;
        }
        return task;
      });
    },
  },
  created() {
    this.tasks = [
      {
        id: 1,
        text: 'Doctors appointment',
        day: 'March 1st at 2:30',
        reminder: true,
      },
      {
        id: 2,
        text: 'Children appointment',
        day: 'June 1st at 4:00',
        reminder: true,
      },
      {
        id: 3,
        text: 'daily checkup',
        day: 'December 3rd at 11:00',
        reminder: false,
      },
    ];
  },
  emits: ['delete-task ,toggle-reminder'],
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
  max-width: 600px;
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
