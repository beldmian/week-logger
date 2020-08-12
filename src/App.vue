<template>
  <div>
    <TaskPicker :days="days" @setEvent="updateTasks"/>
    <WeekdayGrid  :weekdays="weekdays"/>
  </div>
</template>

<script>
import WeekdayGrid from '@/components/WeekdayGrid.vue'
import TaskPicker from '@/components/TaskPicker.vue'
export default {
  data() {
    return {
      days: this.getDaysList(),
      weekdays: [
        {
          day: 'Mon',
          date: ('0' + this.getDaysList()[0].getDate()).slice(-2),
          tasks: [],
          active: this.getDaysList()[0].getDay() == (new Date).getDay(),
        },
        {
          day: 'Tue',
          date: ('0' + this.getDaysList()[1].getDate()).slice(-2),
          tasks: [],
          active: this.getDaysList()[1].getDay() == (new Date).getDay(),
        },
        {
          day: 'Wed',
          date: ('0' + this.getDaysList()[2].getDate()).slice(-2),
          tasks: [],
          active: this.getDaysList()[2].getDay() == (new Date).getDay(),
        },
        {
          day: 'Thu',
          date: ('0' + this.getDaysList()[3].getDate()).slice(-2),
          tasks: [],
          active: this.getDaysList()[3].getDay() == (new Date).getDay(),
        },
        {
          day: 'Fri',
          date: ('0' + this.getDaysList()[4].getDate()).slice(-2),
          tasks: [],
          active: this.getDaysList()[4].getDay() == (new Date).getDay(),
        },
        {
          day: 'Sat',
          date: ('0' + this.getDaysList()[5].getDate()).slice(-2),
          tasks: [],
          active: this.getDaysList()[5].getDay() == (new Date).getDay(),
        },
        {
          day: 'Sun',
          date: ('0' + this.getDaysList()[6].getDate()).slice(-2),
          tasks: [],
          active: this.getDaysList()[6].getDay() == (new Date).getDay(),
        },
      ]
    }
  },
  components: {
    WeekdayGrid,
    TaskPicker
  },
  mounted() {
    if (localStorage.weekdays) {
      this.weekdays = JSON.parse(localStorage.weekdays);
    }
  },
  methods: {
    getDaysList() {
      const curr = new Date; 
      const first = curr.getDate() - curr.getDay() + 1;
      const last = first + 6;
      const firstday = new Date(curr.setDate(first));
      const lastday = new Date(curr.setDate(curr.getDate()+6));
      return this.getDates(firstday, lastday)
    },
    getDates(start, end) {
      for(var arr=[],dt=new Date(start); dt<=end; dt.setDate(dt.getDate()+1)){
          arr.push(new Date(dt));
      }
      return arr;
    },
    updateTasks (task) {
      this.weekdays.filter(day => day.date == task.day)[0].tasks.push({
        status: 'TODO',
        text: task.task
      }),
      localStorage.weekdays = JSON.stringify(this.weekdays)
    }
  }
}
</script>

<style>
body {
  font-family: 'Source Code Pro';
}
</style>