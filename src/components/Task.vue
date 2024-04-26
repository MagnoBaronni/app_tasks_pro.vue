<template>
    <div class="task" @click="$emit('taskChange', task)" :class="stateClass">
    <span @click="$emit('taskDelete', task)" class="close">X</span>
    <p>{{task.name}}</p>
    </div>
</template>

<script>
 export default {
   props:{
    task:{type: Object, required: true}
   },
   computed:{
    stateClass(){
        return{
            pending: this.task.pending,
            done: !this.task.pending
          }
    }
   }
 }
</script>
<style>
.task{
   position: relative;
   box-sizing: border-box;
   widows: 350px;
   height: 150px;
   border-radius: 8px; 
   font-size: 2rem;
   font-weight: 300;
   cursor: pointer;
   user-select: none;
   display: flex;
   justify-content: center;
   align-items: center;
   padding: 30px;
}
.close{
 position: absolute;
 right: 15px;
 top: 5px;
 font-size: 0.9rem;
 font-weight: 600;
 width: 20px;
 height: 20px;
 border-radius: 10px;
 display: flex;
 justify-content: center;
}
.pending{
   border-left: 12px solid #7f120b;
   background-color: #f44336;
}
.done{
    color: #ddd;
 border-left: 12px solid #0a8f08; 
 background-color: #4caf50;
 text-decoration: line-through; 
}

.pending .close{
background-color: #b73229;
}
.done .close{
background-color: #0a8f08;
}


</style>