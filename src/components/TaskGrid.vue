<template>
	<div class="task-grid">
		<template v-if="tasks.length">
			<Task v-for="(task, i) in tasks" :key="task.name" :task="task" @taskDeleted="$emit('taskDeleted', i)" @taskStateChanged="$emit('taskStateChanged', i)"/>
		</template>
		<p v-else class="no-tasks">Sem tarefas</p>	
	</div>
</template>

<script>
import Task from '@/components/Task';

export default {
	components: { Task },
	props: {
		tasks: {type: Array, required: true}
	}
}
</script>

<style>
	body {
		font-family: 'Lato', sans-serif;
		color: #FFF;
	}

	.task-grid {
		display: flex;
		flex-direction: column;
		justify-content: flex-start;
		flex-wrap: wrap;
		width: 90%;
	}

	.task-grid .task {
		margin: 10px;
	}

	.no-task {
		color: #aaa;
		font-size: 1.7rem
	}
	
</style>
