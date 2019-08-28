<template>
  <div id="app">

  <div class="todo_list">
    <Todo v-for="task in tasks" v-bind:task="task"  v-bind:key="task.id" v-on:child-click="deleteTask" />
  </div>

  </div>
  
</template>

<script>
import Todo from './Todo.vue';

export default {
  name: 'app',
  components: {
    Todo
  },
  data(){
    return{
    nowTask:"",
          }
    },
  props:['tasks'],

  methods:{
    deleteTask:function(selectedTask){
      this.nowTask = selectedTask;
      this.$emit('child-click',selectedTask);

  }

}
}
</script>
<style>
.todo_list{
  width: 100%;
  min-height: 70vh;
}

</style>
