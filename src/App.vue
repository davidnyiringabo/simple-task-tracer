<template>
  <div class="container">
    <Header title="Task tracer" @toggle-add-task="toggleAddTask"/>
    <AddTask v-show="showAdddTask" @add-task="addTask"/>
    <Tasks @toggle-reminder="toggleReminder" @delete-task="deleteTask" :tasks = "tasks"/>
  </div>
</template>

<script>

import Header from './components/Header.vue';
import Tasks from './components/Tasks.vue';
import AddTask from './components/AddTask.vue';

export default {
  name: 'App',
  components: {
      Header,
      Tasks,
      AddTask
  },
  data(){
    return {
      tasks: [],
      showAdddTask: false
    }
  },
  methods:{
      deleteTask(id){
        this.tasks = this.tasks.filter(task=>{
          return task.id != id
        })
      },
      toggleReminder(id){
        console.log('task',id)
        this.tasks = this.tasks.map(task=>{
          // console.log(task)
          // if(task.id === id){
          //   console.log(task)
          //   // task.reminder = !task.reminder
          // }
        })
      },
      addTask(data){
        console.log(data)
        this.tasks = [data, ...this.tasks]
      },
      toggleAddTask(){
        this.showAdddTask = !this.showAdddTask
      }
  },
  created(){
    this.tasks = [
      {
        id: 1,
        text: "Doctors appointment",
        day: "March 1st at 2:30PM",
        reminder:true
      },
      {
        id: 2,
        text: "Meeting at school",
        day: "March 1st at 2:30PM",
        reminder: true
      },
      {
        id: 3,
        text: "Food shopping",
        day: "March 1st at 2:30PM",
        reminder: false
      }
    ]
  },
  emits: ['delete-task','toggle-reminder','add-task']
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@300;400&display=swap');

* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  font-family: 'Poppins', sans-serif;
}

.container {
  max-width: 500px;
  margin: 30px auto;
  overflow: auto;
  min-height: 300px;
  border: 1px solid steelblue;
  padding: 30px;
  border-radius: 5px;
}

.btn {
  display: inline-block;
  background: #000;
  color: #fff;
  border: none;
  padding: 10px 20px;
  margin: 5px;
  border-radius: 5px;
  cursor: pointer;
  text-decoration: none;
  font-size: 15px;
  font-family: inherit;
}

.btn:focus {
  outline: none;
}

.btn:active {
  transform: scale(0.98);
}

.btn-block {
  display: block;
  width: 100%;
}
</style>
