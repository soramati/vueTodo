<template>
  <div id="app">
      <TodoList v-bind:tasks="tasks" v-on:child-click="deleteTask"></TodoList>
      <TodoForm v-bind:count="count" v-on:click-child="addTask"></TodoForm>
  </div>
</template>

<script>
import TodoList from './components/TodoList.vue';
import TodoForm from './components/TodoForm.vue';

export default {
  name: 'app',
  components: {
    TodoList,
    TodoForm
  },
  data(){
    return{
    tasks:[{id:1, name:"お兄ちゃんを起こすのです。"}],
    count: 0,
  }
    },
    created:function(){
        this.count = this.tasks.length;
        console.log(this.count);
    },
  methods:{
    addTask:function(newTask){
        this.tasks.push(newTask);
        this.count++;
        console.log(this.tasks);
    },
    deleteTask:function(selectedTask){
    let  n = selectedTask.id;
    let newTasks = [];
    this.tasks.filter(function(task){
        if(task.id !== n){
          newTasks.push(task);
        }
    })
    this.tasks = newTasks;
    this.count--;
    }
  },
}
</script>

<style>

</style>
