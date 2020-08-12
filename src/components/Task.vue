<template>
  <li class="weekday__tasks__task">
    <span class="weekday__tasks__task__status">[{{status.toUpperCase()}}]</span>
    {{text}}
  </li>
</template>

<script>
export default {
  props: {
    text: String,
    status: String,
  }
}
</script>

<style>
.weekday__tasks__task {
  text-align: center;
  padding: 5px;
  border-top: rgb(0, 0, 0) 1px solid;
}

.weekday__tasks__task:last-child{
  border-bottom: rgb(0, 0, 0) 1px solid;
}

.weekday__tasks__task__status {
  font-weight: bold;
}

.weekday__tasks__task__status:hover {
  text-decoration: underline;
}
</style>