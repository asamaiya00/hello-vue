<template>
  <div class="container">
    <nav>
      <Header title="Task Tracker" />
      <Button
        @btn-click="toggleAddTask"
        :label="!showAddTask ? 'Add task' : 'Close'"
        :color="!showAddTask ? 'green' : 'red'"
      />
    </nav>
    <div v-show="showAddTask">
      <AddTask @add-task="addTask" />
    </div>
    <Tasks
      @toggle-reminder="toggleReminder"
      @delete-task="deleteTask"
      :tasks="tasks"
    />
  </div>
</template>

<script>
import Header from './components/Header.vue';
import Button from './components/Button.vue';
import Tasks from './components/Tasks.vue';
import AddTask from './components/AddTask.vue';

export default {
  name: 'App',
  components: {
    Header,
    Button,
    Tasks,
    AddTask,
  },
  data() {
    return {
      tasks: [],
      showAddTask: false,
    };
  },
  methods: {
    deleteTask(id) {
      if (confirm('Are you sure you want to delete?'))
        this.tasks = this.tasks.filter((task) => task.id !== id);
    },
    toggleReminder(id) {
      this.tasks = this.tasks.map((task) =>
        task.id === id ? { ...task, reminder: !task.reminder } : task
      );
    },
    addTask(newTask) {
      this.tasks = [...this.tasks, newTask];
    },
    toggleAddTask() {
      this.showAddTask = !this.showAddTask;
    },
  },
  created() {
    this.tasks = [
      {
        id: 1,
        text: "Doctor's Appointment",
        day: 'May 22nd at 6:00pm',
        reminder: true,
      },
      {
        id: 2,
        text: 'Joining formality',
        day: 'May 24nd at 10:00am',
        reminder: true,
      },
      {
        id: 3,
        text: 'Farewell',
        day: 'May 20nd at 6:00pm',
        reminder: false,
      },
    ];
  },
};
</script>

<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  width: 40%;
  margin: 30px auto;
}

nav {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: center;
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
  font-size: 1rem;
  font-family: inherit;
}

.btn:focus {
  outline: none;
}
.btn:active {
  transform: scale(0.95);
}
.btn-block {
  display: block;
  width: 100%;
}
</style>
