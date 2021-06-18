<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png" />
    
    <div class="container">
      <Header @toggle-add-task="toggleAddTask" :btnText="showAddTask? 'Close window':'Add Task'"  title="Task Tracker"/>

      <div v-show="showAddTask">
        <AddTask  @add-task="addTask"  @hide-add-task-template="toggleAddTask"/>
      </div>

      <Tasks @delete-task="onDeleteTask" @toggle-reminder="toggleReminder" :tasks="tasks"  />

      <Footer/>
    </div>
    
  </div>
</template>

<script>
// @ is an alias to /src
import Header from '../components/Header'
import AddTask from '../components/AddTask'
import Tasks from '../components/Tasks'
import Footer from '../components/Footer'

export default {
  name: "Home",
  components: {
    Header,
    AddTask,
    Tasks,
    Footer

  },
  props:{

  },
  methods:{
    //Toggle Functions
      toggleAddTask(){
        this.showAddTask=!this.showAddTask
      },
      
      toggleReminder(id){
        if(confirm('Task Completed?')){
                console.log(id)
        }
      },
    //CRUD Operations
      addTask(newTask){
        this.tasks=[...this.tasks,newTask]
        this.toggleAddTask()
      },
      onDeleteTask(id){
        if(confirm('Are you sure?')){
            console.log(id)
            this.tasks=this.tasks.filter((task)=> task.id!=id)
        }
      },
  },
  data(){
    return {
      tasks:[],
      showAddTask:false
    }
  },
  created(){
        
    this.tasks=[
      {
        id:1,text:"This is it.",day:"Sunday",reminder:true
      },
      {
        id:2,text:"This is it.",day:"Monday",reminder:true
      },
      {
        id:3,text:"This is it.",day:"Tuesday",reminder:true
      },
      {
        id:4,text:"This is it.",day:"Wednesday",reminder:false
      }
    ]
  }
};
</script>