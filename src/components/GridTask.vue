<template>
    <div class="task-grid">
        <template v-if="tasks.length">
           <Task v-for="(task, i) in tasks" 
           :key="task.name" 
           @taskDelete="$emit('taskDelete', i)"
           @taskChange="$emit('taskChange', i)" 
           :task="task">   
          </Task>
      </template>
    <p v-else class="no-task">Suas tarefas estão em dia ;)</p>
    </div>
</template>

<script>
import Task from './Task.vue'
 export default {
    components:{Task},
    props:{
       tasks:{ type: Array,  required: true}
    },
   
 }
</script>
<style>
.task-grid{
   display:flex;
   justify-content: center;
   flex-wrap: wrap;
}
.task-grid .task{
   margin: 10px;
}
.no-task{
    font-size: 1.7rem;
    color-scheme: #aaa;
}


</style>