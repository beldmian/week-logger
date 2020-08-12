<template>
  <div class="weekday">
    <div class="weekday__title" :class="{active: active}">
      <span>{{weekday}} </span>
      <strong>{{date}}</strong>
    </div>
    <strong v-if="tasks">Tasks: </strong>
    <Tasklist :tasks="tasks"></Tasklist>
  </div>
</template>

<script>
import Tasklist from '@/components/Tasklist.vue'
export default {
  props: {
    'weekday': String,
    'date': String,
    'tasks': Array,
    'active': Boolean,
  },
  components: {
    Tasklist
  }
}
</script>

<style>
.weekday__title {
  padding: 10px;
}

.weekday__title.active {
  background-color: rgb(243, 243, 243);
}

.weekday {
  text-align: center;
}
</style>