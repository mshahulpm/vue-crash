<template>
    <form @submit="onSubmit">
        <input v-model="text" type="text" placeholder="add task.." />
        <input v-model="day" type="text" placeholder="Day & Time ..." />
        <label>Set reminder</label>
        <input v-model="reminder" type="checkbox" />
        <button type="submit">Save task</button>
    </form>
</template>

<script>
export default {
    name:"AddTask",
    data(){
        return {
            text:"",
            day:"",
            reminder:false
        }
    },
    methods:{
        onSubmit(e){
            e.preventDefault()
            if(!this.text){
                alert('please add a task')
                return
            }

            const newTask = {
                text:this.text,
                day:this.day,
                reminder:this.reminder
            }

            this.$emit('add-task',newTask);

            this.text=''
            this.day=''
            this.reminder=false
        }
    }
}
</script>
<style scoped>
form{
    max-width: 350px;
    padding: 10px;
    box-shadow: 1px 1px 10px 5px gray;
    border: 1px solid gainsboro;
    border-radius: 4px;
    margin: 20px auto;
}
form * {
    margin-left: 10px;
}
input[type='text']{
 display: block;
 margin:10px ;
 width: 80%;
 font-weight: 700;
}
button{
    display: block;
    margin: 10px;
    margin-left: auto;
    margin-right: 30px;
    background: royalblue;
    border-radius: 4px;
    box-shadow: 1px 1px 10px 5px gray;
    border: none;
    outline: none;
    color: white;
    padding: 3px 7px;
    font-size: 1rem;
    cursor: pointer;
}
</style>