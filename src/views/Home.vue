<template>
  <AddTask v-show="showAddTask" @add-task="addTask" />
  <Tasks @toggle-reminder='toggleReminder' @delete-task='deleteTask' :tasks="tasks"/>
</template>

<script>
import Tasks from './components/Tasks'
import AddTask from './components/AddTask'

export default {
    name: 'Home',
    components: {
      Tasks,
      AddTask
    }
}
</script>