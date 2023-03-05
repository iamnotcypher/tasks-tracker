<template>
  <div class="container">
    <Header :showAddTask="showAddTask" @toggle-task="toggleTask" title="Task Tracker"/>
    <AddTask v-show="showAddTask" @add-task="addTask" />
    <Tasks @toggle-reminder='toggleReminder' @delete-task='deleteTask' :tasks="tasks"/>
  </div>
</template>

<script>
import Header from './components/Header'
import Tasks from './components/Tasks'
import AddTask from './components/AddTask'


export default {
  name: "App",
  components: {
    Header,
    Tasks,
    AddTask
  },
  data() {
    return {
      tasks: [],
      showAddTask: false
    }
  },
  methods: {
    addTask(task) {
      this.tasks = [ ...this.tasks, task] 
    },
    toggleTask() {
      this.showAddTask = !this.showAddTask
    },
    deleteTask(id) {
      if(confirm('are you sure!?')) {
        this.tasks = this.tasks.filter((task) => task.id !== id)
      }
    },
    toggleReminder(id) {
      this.tasks = this.tasks.map(task => task.id === id ? { ...task, reminder: !task.reminder} : task)
    },
    async fetchTasks() {
      const res = await fetch('http://localhost:8000/tasks')
      const data = await res.json()

      return data;
    },
    async fetchTask(id) {
      const res = await fetch(`http://localhost:8000/tasks/${id}`)
      const data = await res.json()

      return data;
    }
  },
  async created() {
    this.tasks = await this.fetchTasks()
  }
};
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@400;500&display=swap');
#app {
  font-family: "Poppins", sans-serif;
  color: #2c3e50;
}
* {
  margin:0;
  padding: 0;
  box-sizing: border-box;
}
.container {
  max-width: 500px;
  margin: 30px auto;
  overflow: auto;
  min-height: 300px;
  border: 1px solid steelblue;
  padding: 30px;
  border-radius: 3px;
}
.btn {
  display: inline-block;
  background: #000;
  color: #fff;
  border: none;
  padding: 10px 20px;
  margin: 5px;
  border-radius: 4px;
  cursor: pointer;
  text-decoration: none;
  font-size: 15px;
  font-family: inherit;
}
.btn:focus {
  outline: none;
}
</style>
