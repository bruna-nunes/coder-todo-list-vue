
<template>
	<div id="app">
		<Header />
		<TasksProgress :progress="progress"/>
		<NewTask @taskAdded="addTask"/>
		<TaskGrid :tasks="tasks" @taskDeleted="deleteTask" @taskStateChanged="toggleTaskState"/>
	</div>
</template>

<script>
import Header from '@/components/Header';
import TasksProgress from '@/components/TasksProgress';
import NewTask from '@/components/NewTask';
import TaskGrid from '@/components/TaskGrid';

export default {
	components: {Header, TasksProgress, NewTask, TaskGrid},
	data(){
		return {
			tasks: []
		}
	},
	watch: {
		tasks: {
			deep: true, //analise mais profunda do objeto, permite perceber mudancas de estado e nao so de inclusao/exclusao
			handler(){
				localStorage.setItem('tasks', JSON.stringify(this.tasks))
			}
		}
	},
	computed: {
		progress(){
			const total = this.tasks.length;
			const done = this.tasks.filter(t => !t.pending).length;
			return Math.round(done/total * 100) || 0
		}
	},
	methods: {
		addTask(task) {
			const sameName = t => t.name === task.name;
			const reallyName = this.tasks.filter(sameName).length == 0
			if(task.name!='' && reallyName){
				this.tasks.push({
					name: task.name,
					pending: task.pending || true
				});
			}
			
		},
		deleteTask(i){
			this.tasks.splice(i, 1)
		},
		toggleTaskState(i) {
			this.tasks[i].pending = !this.tasks[i].pending
		}
	},
	created(){
		const json = localStorage.getItem('tasks');
		this.tasks = JSON.parse(json) || [];
	}
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Signika:wght@300&display=swap');

	body {
		font-family: 'Lato', sans-serif;
		color: #FFF;
		padding: 0;
		margin: 0;
		font-family: 'Signika', sans-serif;
	}

	#app {
		display: flex;
		flex: 1;
		flex-direction: column;
		justify-content: flex-start;
		align-items: flex-start;
		height: 100vh;
	}

	#app h1 {
		margin-bottom: 5px;
		font-weight: 300;
		font-size: 3rem;
	}
</style>
