<template>
	<div class="header" >
		<p>to-do</p>
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


	.header {
		width: 100%;
		height: 45px;
		background-color: #9c88ff;
		display: flex;
		justify-content: flex-start;
		align-items: center;
		padding: 10px;
		box-sizing: border-box;
		font-size: 1.8rem
	}
</style>
