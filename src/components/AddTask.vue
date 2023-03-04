<template>
  <form class="add-form">
    <div class="form-control">
      <label>Task</label>
      <input type="text" name="text" placeholder="Add Task" />
    </div>
    <div class="form-control">
      <label>Day & Time</label>
      <input type="text" name="day" placeholder="Add Day & Time" />
    </div>
    <div class="form-control form-control-check">
      <label>Reminder</label>
      <input type="checkbox" name="reminder" placeholder="Add Task" />
    </div>
    <input class="btn btn-block" type="submit" value="Save Task">
  </form>
</template>

<script>
export default {
  name: "AddTask"
}
</script>