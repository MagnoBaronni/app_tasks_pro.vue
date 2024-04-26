<template>
	<div id="app">
		<h1>Tarefas</h1>
		<Progress :progress="Taskprogress"></Progress>
		<NewTask @addNewTask="saveTasck" />
		<GridTask 
		@taskDelete="deleteTask"
		@taskChange="taskStateChange"
		:tasks="tasks"
		/>
	</div>
</template>
<script>
import Progress from './components/Progress.vue'
import NewTask from './components/NewTask.vue'
import GridTask from './components/GridTask.vue'

export default {
components:{Progress, NewTask, GridTask},

data(){
	return { 
		tasks: []
	}
},
//-------------------------------------------------------------------------------------------------------------
	computed:{
		Taskprogress(){ 
			const total = this.tasks.length
			const done = this.tasks.filter(task => !task.pending).length
			return Math.round(done / total * 100) || 0
		},
	},

//-------------------------------------------------------------------------------------------------------------   
   watch:{
	tasks:{
		deep: true,
		handler(){
			localStorage.setItem('tasks', JSON.stringify(this.tasks))
		}
	}
   },

//-------------------------------------------------------------------------------------------------------------  
   methods:{
		saveTasck(task){
		const sameName = tks => tks.name === task.name	
		const changeTask = this.tasks.filter(sameName).length == 0
		if(changeTask){
			this.tasks.push({
				name: task.name,
				pending: task.pending || true
			})
		}
	},

//-------------------------------- -----------------------------------------------------------------------------
	deleteTask(i){
	this.tasks.splice(i, 1)
		},
	taskStateChange(i){
	this.tasks[i].pending = !this.tasks[i].pending
		}
	},
//-------------------------------------------------------------------------------------------------------------
	created(){
	const json =localStorage.getItem('tasks')
	const array = JSON.parse(json)
	this.tasks = Array.isArray(array)? array : []
	}
	}
</script>

<style>
	body {
		font-family: 'Lato', sans-serif;
		background: linear-gradient(to right, rgb(22, 34, 42), rgb(58, 96, 115));
		color: #FFF;
	}

	#app {
		display: flex;
		flex: 1;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		height: 100vh;
	}

	#app h1 {
		margin-bottom: 5px;
		font-weight: 300;
		font-size: 3rem;
	}
</style>
