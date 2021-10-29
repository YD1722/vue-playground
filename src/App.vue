<template>
  <div class="container">
    <Header
      @toggle-task-add="toggleAddTask"
      @reload-tasks="reloadAllTasks"
      title="Task Tracker"
      :is-show-add-task-form="isShowAddTaskForm"
    />
    <div v-if="isShowAddTaskForm">
      <TaskForm @new-task="onAddNewTask" />
    </div>
    <TaskList
      @toggle-reminder="onToggleReminder"
      @delete-task="onDeleteTask"
      :tasks="tasks"
    />
  </div>
</template>

<script>
import Header from './components/Header';
import TaskList from './components/TaskList';
import TaskForm from './components/TaskForm';

export default {
  name: 'App',
  components: {
    TaskList,
    Header,
    TaskForm,
  },
  data() {
    return {
      tasks: [],
      isShowAddTaskForm: false,
    };
  },
  methods: {
    onDeleteTask(id) {
      this.tasks = this.tasks.filter((task) => task.id !== id);
    },
    onToggleReminder(id) {
      console.log('reminder', id);
      this.tasks = this.tasks.map((task) =>
        task.id === id ? { ...task, reminder: !task.reminder } : task
      );
    },
    onAddNewTask(newTask) {
      console.log('new-task', newTask);
      this.tasks.push(newTask);
    },
    toggleAddTask() {
      this.isShowAddTaskForm = !this.isShowAddTaskForm;
    },
    reloadAllTasks() {},
  },
  created() {
    this.tasks = [
      {
        id: 1,
        text: 'Meet doctor',
        day: 'Oct 25, 2021',
        reminder: true,
      },
      {
        id: 2,
        text: 'Meet plumber',
        day: 'Oct 25, 2021',
        reminder: false,
      },
      {
        id: 3,
        text: 'Sleep',
        day: 'Oct 25, 2021',
        reminder: false,
      },
    ];
  },
};
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@300;400&display=swap');

* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  font-family: 'Poppins', sans-serif;
}

.container {
  max-width: 70%;
  margin: 30px auto;
  overflow: auto;
  min-height: 300px;
  border: 1px solid steelblue;
  padding: 30px;
  border-radius: 5px;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
