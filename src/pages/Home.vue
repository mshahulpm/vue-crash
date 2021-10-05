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
      const res =await fetch(`api/tasks/${id}`,{
        method:"delete"
      })
      res.status===200?(      this.tasks = this.tasks.filter(t=>t.id!==id)):alert('somthing wrong')
}
    },

   async toggleReminder(id){
      const task = await( await this.fetchTask(id) ).json()
      let newTask = {...task,reminder:!task.reminder}
      if(task.id){
        const updatedTask = await fetch('api/tasks/'+id,{
          method:"put",
          headers:{
            'Content-type':'application/json'
          } ,
          body:JSON.stringify(newTask)
        })
        console.log(updatedTask);
      this.tasks=this.tasks.map(t=>t.id===id?{...t,reminder:!t.reminder}:t)
      } 
    },


  async addTask(data){

      const res =await( await fetch('api/tasks',{
        method:"post",
        headers:{
          'Content-type':'application/json',
        },
          body : JSON.stringify(data)

      })).json()
     this.tasks.push(res)
     this.showAddTask=false
},
async fetchTasks(){
  const res = await(await fetch('api/tasks')).json()
   this.tasks = res
},

async fetchTask (id){
   return await fetch(`api/tasks/${id}`)
}

  },
  created(){
    this.fetchTasks()
   
  }
}
</script>



