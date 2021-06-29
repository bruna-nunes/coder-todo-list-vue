<template>
	<div class="task" :class="stateClass" @click="$emit('taskStateChanged', task)">
		<span @click.stop="$emit('taskDeleted', task)" class="close"><i class="fas fa-trash"></i></span>
		<p>{{task.name}}</p>
	</div>
</template>

<script>
export default {
	props: {
		task: {type: Object, required: true}
	},
	computed: {
		stateClass() {
			return {
				pending: this.task.pending,
				done: !this.task.pending
			}
		}
	}
}
</script>

<style>
	body {
		font-family: 'Lato', sans-serif;
		color: #FFF;
	}

	.task {
		position: relative;
		box-sizing: border-box;
		width: 100%;
		height: auto;
		padding: 5px 5px 5px 10px;
		border-radius: 2px;
		font-size: 1.2rem;
		font-weight: 300;
		cursor: pointer;
		user-select: none;
		display: flex;
		justify-content: flex-start;
		align-items: center;
		background: rgb(230, 230, 230);
		color: rgb(92, 92, 92);
	}
	
	.done {
		border-left: 4px solid #62d67b;
		text-decoration: line-through;
 	}

	.pending {
		border-left: 4px solid #b73229;		
	}
	
	.pending .close {
		
	}

	.done .close{
		
	}

	.close {
		position: absolute;
		right: 10px;
		top: 10px;
		font-size: 0.9rem;
		font-weight: 600;
		height: 20px;
		width: 20px;
		border-radius: 10px;
		display: flex;
		justify-content: center;
		color: #9c88ff;
	}
</style>
