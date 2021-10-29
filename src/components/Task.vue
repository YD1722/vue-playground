<template>
  <div
    @dblclick="$emit('toggle-reminder', taskDetails.id)"
    :class="[taskDetails.reminder ? 'reminder' : '', 'task']"
  >
    <h3>
      {{ taskDetails.text }}
      <i @click="$emit('delete-task', taskDetails.id)" class="fa fa-times"></i>
    </h3>
    <span>{{ taskDetails.day }}</span>
  </div>
</template>

<script>
export default {
  name: 'Task',
  props: {
    taskDetails: {
      id: String,
      text: String,
      reminder: Boolean,
    },
  },
};
</script>

<style scoped>
.fa {
  color: red;
}

.task {
  background: #f4f4f4;
  margin: 5px;
  padding: 10px 20px;
  cursor: pointer;
}

.task.reminder {
  border-left: 5px solid green;
}

.task h3 {
  display: flex;
  align-items: center;
  justify-content: space-between;
}
</style>
