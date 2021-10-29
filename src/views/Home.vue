<template>
  <TaskForm v-show="isShowAddTaskForm" />
  <TaskList
    @toggle-reminder="onToggleReminder"
    @delete-task="onDeleteTask"
    :tasks="tasks"
  />
</template>

<script>
import TaskList from '../components/TaskList';
import TaskForm from '../components/TaskForm';

export default {
  name: 'App',
  props: {
    isShowAddTaskForm: Boolean,
  },
  components: {
    TaskList,
    TaskForm,
  },
  data() {
    return {
      tasks: [],
    };
  },
  methods: {
    onDeleteTask(id) {
      this.tasks = this.tasks.filter((task) => task.id !== id);
    },
    onToggleReminder(id) {
      this.tasks = this.tasks.map((task) =>
        task.id === id ? { ...task, reminder: !task.reminder } : task
      );
    },
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
