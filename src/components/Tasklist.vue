<template>
  <ul class="weekdays__tasks">
    <Task v-for="task in tasks" :key="task.text" :text="task.text" :status="task.status"></Task>
  </ul>
</template>

<script>
import Task from '@/components/Task.vue'
export default {
  props: {
    tasks: Array,
  },
  components: {
    Task
  }
}
</script>

<style>
.weekdays__tasks {
  list-style: none;
  margin: 0;
  padding: 0;
}
</style>