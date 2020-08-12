<template>
  <div class="grid">
    <Weekday v-for="weekday in weekdays" :key="weekday.day" :weekday="weekday.day" :date="weekday.date" :tasks="weekday.tasks" :active="weekday.active"/>
  </div>
</template>

<script>
import Weekday from '@/components/Weekday'
export default {
  props: {
    weekdays: Array
  },
  components: {
    Weekday
  } 
}
</script>

<style>
.grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(100px, 1fr));
}
</style>