<template>
<div @dblclick="$emit('toggle-reminder',task.id)" :class="[task.reminder?'task-reminder':'','task']">
<h3>
    {{task.text}}
    <i @click="$emit('delete-task',task.id)" class="far fa-times-circle"></i>
</h3>
<p>{{task.day}}</p>
</div>
    
</template>

<script>
export default {
    name:"Task",
    props:{
        task:Object
    },
   
}
</script>

<style scoped>
.far {
    color: red;
    font-weight: 700;
    font-size: 1.5rem;
}
.task{
    background: #dfe6df;
    margin:5px;
    padding: 10px 20px;
    cursor: pointer;
}
.task-reminder{
    border-left: 5px solid green;
}
.task h3{
    display: flex;
    align-items: center;
    justify-content: space-between;
}
</style>