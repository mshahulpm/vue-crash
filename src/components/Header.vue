<template>
    <header>
        <h1> {{title}}</h1>
        <Button @toggle-form="$emit('toggle-form')" @click="btnFunc" text="Add Task" color="green" />
    </header>
</template>


<script>
import Button from './Button'

export default {
    name: "Header",
    props:{
        
        title : {
            type:String,
            default:"Task Buddy"
        },
        btnFunc : Function
    },
    components:{
        Button
    }
}
</script>

<style scoped>
header{
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 20px;
}
</style>