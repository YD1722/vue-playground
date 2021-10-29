<template>
  <header>
    <h1>{{ title }}</h1>

    <div class="btn-container">
      <Button
        @click="onAdd"
        :btnText="isShowAddTaskForm ? 'Close' : 'Add Task'"
        :color="isShowAddTaskForm ? 'red' : 'green'"
      ></Button>
      <Button @click="onReload" btnText="Reload Tasks"></Button>
    </div>
  </header>
</template>

<script>
import Button from './Button';

export default {
  name: 'Header',
  components: { Button },
  props: {
    title: {
      type: String,
      default: 'Hello World',
    },
    isShowAddTaskForm: Boolean,
  },
  methods: {
    onAdd(e) {
      this.$emit('toggle-task-add', e);
    },
    onReload(e) {
      this.$emit('reload-tasks', e);
    },
  },
};
</script>

<style scoped>
header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 20px;
}

.btn-container{
  width: 40%;
  display: flex;
  justify-content: space-between;
}
</style>
