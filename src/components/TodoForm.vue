<template>
<div class="form">
    <v-text-field
    v-model="newTask" 
      label="Todo"
      @keyup.enter="addTask"
      class="test_form"

    ></v-text-field>
    <v-btn
      color="success"
      class="mr-4"
      v-on:click="addTask"
    >追加</v-btn>
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
.form{
    max-width: 1000px;
    min-width: 40vw;
}
</style>
