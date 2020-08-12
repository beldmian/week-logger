<template>
<div>
  <select v-model="day">
    <option value="" selected disabled hidden>Day</option>
    <option v-for="day in days" :key="day.toISOString()">
      {{('0' + day.getDate()).slice(-2)}} 
    </option>
   </select>
  <input type="text" v-model="task">
  <button @click="emit" >Отправить</button>
</div>
</template>

<script>
export default {
  props: {
    days: Array
  },
  data() {
    return {
      day: '',
      task: ''
    }
  },
  methods: {
    emit() {
      this.$emit('setEvent', {
        day: this.day,
        task: this.task,
      })
      this.day = ''
      this.task =''
    }
  }
}
</script>

<style scoped>
input[type=text] {
  width: 20%;
  padding: 12px 20px;
  margin: 8px;
  box-sizing: border-box;
}
select {
  width: 5%;
  padding: 12px 5px;
  border: none;
  background-color: #4CAF50;
  color: #fff;
}
button {
  background-color: #4CAF50;
  border: none;
  color: white;
  padding: 14px 32px;
  text-decoration: none;
  margin: 4px 2px;
  cursor: pointer;
}
</style>