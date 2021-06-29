<template>
	<div class="new-task">
		<input v-model="name" type="text" @keydown.enter="add" class="form-element" placeholder="Nova tarefa">
		<button @click="add" class="form-element">+</button>
	</div>
</template>

<script>
export default {
	data(){
		return {
			name: ''
		}
	},
	methods: {
		add() {
			this.$emit('taskAdded', {name: this.name});
			this.name = '';	
		}
	}
}
</script>

<style>
	body {
		font-family: 'Lato', sans-serif;
		color: #FFF;
	}

	.new-task {
		margin: 15px 0px 15px 10px;
	}

	.form-element {
		outline: none;
		font-size: 1em;
		border: 1px solid #fff;
		padding: 5px 10px 8px;
	}
	input.form-element {
		width: 500px;
		background: rgb(243, 243, 243);;
		border-top-right-radius: 5px;
		border-top-left-radius: 5px;
		border-bottom: 2px solid #9c88ff;
		padding: 10px;
		margin-right: 10px;
		color: #9c88ff;
	}
	button.form-element {
		border-left:none;
		background: #9c88ff;
		border-radius: 100%;
		padding: 10px 15px;
		color: #fff;
		font-size: 1.2em;
	}
</style>
