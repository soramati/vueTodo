<template>

<div  class="task">
<v-card   class="mx-auto task_card">
    <v-card-title><span class="delete" v-on:click="deleteTask">    <v-checkbox></v-checkbox>

</span>{{task.name}}</v-card-title>

</v-card>
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
.task{
  margin: 30px 40px;
}
.task_card{
  width: 500px; 
  padding: 15px 10px;
}
.delete{
  padding-right: 30px;
}
</style>
