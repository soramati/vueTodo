<template>

<div  class="task">
    <p>タスク{{task.id}}：{{task.name}}<span v-on:click="deleteTask">×</span></p> 
</div>
</template>

<script>
export default {
  name: 'Todo',
  props: ['task'],
methods: {
  deleteTask:function(){
    const selectedTask = this.task;
    this.$emit('child-click',selectedTask);

  }
}
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.task p {
  font-size: 2rem
}
</style>
