<template>
	<div class="container">
		<div class="left"><span></span></div>
		<h3>{{titleName}}</h3>
		<div class="right"><span></span></div>
	</div>
</template>
<script>
	export default{
		props: ["titleName"]
	}
</script>
<style scoped>
	.container{
		overflow: hidden;
		width: 90%;
		position: relative;
		height: 30px;
	}
	.left,.right{
		position: absolute;
		top: 50%;
		height: 1px;
		width: 45%;
		box-sizing: border-box;
		border: solid 1px #e2e2e2;
	}
	.right{
		right: 0
	}
	h3{
		width: 10%;
		text-align: center;
		position: absolute;
		left: 45%;
		height: 100%;
		margin: 0;
		line-height: 30px; 
		font-size: 24px;
		font-weight: bold
	}
	span{
		width: 16px;
		height: 16px;
		background-color: #e2e2e2;
		border-radius: 8px;
		display: block;
		position: relative;
		top: -8px;
	}
	.left span{
		float: right;
		right: -5px
	}
	.right span{
		left: -5px
	}
</style>