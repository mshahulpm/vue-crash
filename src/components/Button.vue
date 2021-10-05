<template>
    <button @click="$emit('toggle-form')"  class="btn" :style="{background:color}">{{text}}</button>
</template>

<script>
export default {
    name:"Button",
    props:{
        text:String,
        color:String
    },
   
}
</script>

<style scoped>
.btn{
padding: 5px 10px;
font-weight: 550;
margin: 5px;
margin-right: 20px;
border-radius: 4px;
border: none;
outline: none;
box-shadow: 0px 0px 5px 1px rgb(167, 160, 160);
color: white;
font-size: 1rem;
cursor: pointer;
}
</style>