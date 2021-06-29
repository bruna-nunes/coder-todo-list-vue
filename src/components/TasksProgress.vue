<template>
	<div class="tasksProgress">
		<p class="text-andamento"> Andamento das tarefas: </p>
		<div class="tasks-progress" >
			<p class="progress-value">{{progress}}%</p>
			<div class="progress-bar" :style="{width: progress + '%'}"></div>
		</div>
	</div>
</template>

<script>
export default {
	props: {
		progress: {type: Number, default: 0}
	},
}
</script>

<style>
	.text-andamento {
		color: #856dff;
		font-weight: bold;
	}
	.tasksProgress {
		width: 100%;
		display: flex;
		align-items: center;
		color: rgb(51, 51, 51);
		padding: 5px 10px 5px 10px;
	}

	.tasks-progress{
		position: relative;
		width:40%;
		height: 30px;
		background: rgb(224, 224, 224);
		color: rgb(156, 156, 156);
		border-radius: 8px;
		margin: 15px 0px 15px 10px;
		display: flex;
		flex-direction: column;
		align-items: center;
	}

	.progress-bar {
		position: absolute;
		border-radius: 8px;
		height: 100%;
		background-color: #78e08f;
		align-self: flex-start;
	}

	.progress-value {
		z-index: 1;
		margin-top: 5px
	}
</style>
