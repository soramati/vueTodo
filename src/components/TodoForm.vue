<template>
<div class="form">
      <input  v-model="newTask" @keyup.enter="addTask" type="text">
      <v-btn v-on:click="addTask">作成</v-btn> 
</div>
</template>

<script>


export default {
  name: 'TodoForm',

data() {
  return {
    newTask:"",
  }
},
props:['count'],
methods: {

  addTask:function(){
     const id = this.count+1;
     const name = this.newTask;
     const newTask = {id:id,name:name};
     this.$emit('click-child',newTask);
     console.log(newTask);


  },
}
}
</script>

<style>

</style>
