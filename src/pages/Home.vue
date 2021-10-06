<template>
     <Header  title="Task Tracker" @toggle-form="()=>this.showAddTask=!this.showAddTask" />
  <div v-show="showAddTask">
  <AddTask @add-task="addTask"/>
  </div>
  <Tasks @toggle-reminder="toggleReminder" @delete-task='deleteTask' :tasks="tasks"/>
</template>

<script>
import Header from '../components/Header'
import Tasks from '../components/Tasks'
import AddTask from '../components/AddTask'

export default {
    name:"Home",
    components:{
    Header,    
    Tasks,
    AddTask,
    },
     data(){
    return {
      tasks :[],
      showAddTask:false
    }
  },
  methods:{
   async deleteTask(id){
      if(confirm('Are u sure ?')){
      let tasks =JSON.parse(localStorage.getItem('tasks'))
      tasks = tasks.filter(t=>t.id!==id)
      localStorage.setItem('tasks',JSON.stringify(tasks))
      this.tasks = tasks    
}
    },

   async toggleReminder(id){
     
        this.tasks = this.tasks.map(t=>t.id===id?{...t,reminder:!t.reminder}:t)
        localStorage.setItem('tasks',JSON.stringify(this.tasks))
    },
  async addTask(data){

      data.id = this.tasks.length
      this.tasks.push(data)
      localStorage.setItem('tasks',JSON.stringify(this.tasks))
},
async fetchTasks(){
  const res = JSON.parse(localStorage.getItem('tasks'))
  if(!res) localStorage.setItem('tasks',JSON.stringify([]))
   this.tasks = res||[]
},

async fetchTask (id){
   return this.tasks.find(t=>t.id===id)
}

  },
  created(){
    this.fetchTasks()
   
  }
}
</script>



