<template>
    <div class="new-task">
        <input class="form-task" v-model="name" type="text" placeholder="Nova tarefa" @keydown.enter="addNew">
        <button class="form-task" @click="addNew">+</button>
    </div>
</template>

<script>
 export default {
    data(){
        return {
        name:''
    }
    },
   methods:{
        addNew(){
          this.$emit('addNewTask', {name: this.name})
          this.name = ''
        }
    }
 }
</script>
<style>
.new-task{
    margin: 35px;
}
.form-task{
outline: none;
font-size: 2rem;
border:1px solid #fff;
padding: 5px 10px 8px;
color: #fff
}

input.form-task{
width: 500px;
border-top-left-radius: 8px;
border-bottom-left-radius: 8px;
background: #fff2;
}
button.form-task{      
border-left: none;
background-color: #2196f3;
border-top-right-radius: 8px;
border-bottom-right-radius: 8px;
cursor: pointer;
}

</style>