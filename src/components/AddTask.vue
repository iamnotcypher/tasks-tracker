<template>
  <form @submit="onSubmit" class="add-form">
    <div class="form-control">
      <label>Task</label>
      <input v-model="text" type="text" name="text" placeholder="Add Task" />
    </div>
    <div class="form-control">
      <label>Day & Time</label>
      <input v-model="date" type="text" name="day" placeholder="Add Day & Time" />
    </div>
    <div class="form-control form-control-check">
      <label>Reminder</label>
      <input v-model="reminder" type="checkbox" name="reminder" placeholder="Add Task" />
    </div>
    <input class="btn btn-block" type="submit" value="Save Task">
  </form>
</template>

<script>
export default {
  name: "AddTask",
  data() {
    return {
      text: '',
      date: '',
      reminder: false
    }
  },
  methods: {
    onSubmit(e) {
      e.preventDefault()

      if(!this.text || !this.date) {
        alert("Please add a task")
        return
      }

      const newTask = {
        text: this.text,
        date: this.date,
        reminder: this.reminder
      }
      this.$emit('add-task', newTask)
      this.text = ''
      this.date = ''
      this.reminder = ''

    }
  }
}
</script>

<style scoped>
  .add-form {
    margin-bottom: 40px;
  }
  .form-control {
    margin: 20px 0;
  }
  .form-control label {
    display: block;
  }
  .form-control input {
    width: 100%;
    height: 40px;
    margin: 5px;
    padding: 3px 7px;
    font-size: 17px;
  }
  .form-control-check {
    display: flex;
    align-items: center;
    justify-content: space-between;
  }
  .form-control-check label {
    flex: 1;
  }
  .form-control-check input {
    flex: 2;
    height: 20px
  }
  .btn-block {
    display: block;
    width: 100%;
  }
</style>