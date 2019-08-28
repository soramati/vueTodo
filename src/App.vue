<template>
  <div id="app">
 <v-app>
    <v-content>
        <transition name="alert">
            　<v-alert  v-show="alert" type="success" class="alert">
            Todoを追加しました('◇')ゞ
            </v-alert>
        </transition>  
    <v-card class="overflow-hidden">
    <v-app-bar
      absolute
      color="white"
      elevate-on-scroll
      scroll-target="#scrolling-techniques-7"
    >
      <v-app-bar-nav-icon></v-app-bar-nav-icon>

      <v-toolbar-title>Todo</v-toolbar-title>

      <div class="flex-grow-1"></div>


    </v-app-bar>
    <v-sheet
      id="scrolling-techniques-7"
      class="overflow-y-auto"
    >
      <v-container class="fram" style="height: 100vh;">
        <TodoList v-bind:tasks="tasks" v-on:child-click="deleteTask"></TodoList>
        <TodoForm v-bind:count="count" v-on:click-child="addTask"></TodoForm>

      </v-container>
    </v-sheet>
  </v-card>
    </v-content>
  </v-app>
  </div>

  
</template>

<script>
import TodoList from './components/TodoList.vue';
import TodoForm from './components/TodoForm.vue';
import { setTimeout } from 'timers';

export default {
  name: 'app',
  components: {
    TodoList,
    TodoForm,
  },
  data(){
    return{
    alert:false,
    tasks:[{id:1, name:"タスクを入力してください(*´▽｀*)"}],
    count: 0,
  }
    },
    created:function(){
        this.count = this.tasks.length;
    },
  methods:{
    addTask:function(newTask){
        this.tasks.push(newTask);
        this.count++;
        this.alert = true;
        setTimeout(this.alertOut,3000);
          
    },
    alertOut:function(){
      this.alert = false;
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
.fram{
  max-width: 1000px;
  min-width: 80vw;
  display: flex;
  align-items: center;
  flex-direction: column;
  justify-content: center;
}
.alert{
  position: fixed;
  top: 0;
  left: 0;
  z-index: 10;
  width: 100vw;
  }
.alert-enter{
  transform: translateY(-100%);
}
.alert-enter-active{
   transition:transform 0.5s;

}
.alert-enter-to{
  transform: translateY(0);
}
.alert-leave{
  transform: translateY(0);
  
}
.alert-leave-to{
  transform: translateY(-100%);
}
.alert-leave-active{
   transition:transform 0.5s;

  
}
</style>
