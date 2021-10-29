<template>
  <div class="container">
    <Header
      @toggle-task-add="toggleAddTask"
      @reload-tasks="reloadAllTasks"
      title="Task Tracker"
      :is-show-add-task-form="isShowAddTaskForm"
    />
    <router-view :isShowAddTaskForm="isShowAddTaskForm"></router-view>
    <Footer />
  </div>
</template>

<script>
import Header from './components/Header';
import Footer from './components/Footer'

export default {
  name: 'App',
  components: {
    Header,
    Footer
  },
  data() {
    return {
      isShowAddTaskForm: false,
    };
  },
  methods: {
    toggleAddTask() {
      this.isShowAddTaskForm = !this.isShowAddTaskForm;
    },
    reloadAllTasks() {},
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
