<template>
  <div @dblclick="$emit('toggle-reminder', task.id)" class="task" :class="[task.reminder ? 'reminder' : '']">
    <h3>
      {{ task.text }}
      <i @click="$emit('delete-task',task.id)" class="fas fa-times"></i>
    </h3>
    <p>{{ task.date }}</p>
  </div>
</template>

<script>
export default {
  name: "Task",
  props: {
    task: Object
  }
}
</script>

<style scoped>
  .fas {
    color: crimson;
  }
  .task {
    background: #f4f4f4;
    margin: 5px;
    padding: 10px 20px;
    cursor: pointer;
  }
  .task.reminder {
    border-left: 5px solid teal;
  }
  .task h3 {
    display: flex;
    align-items: center;
    justify-content: space-between;
  }
</style>