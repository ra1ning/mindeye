<template>
	<div class="item">
		<div class="top" :style="'background:url('+require('../assets/blueline.png')+') repeat-x bottom'">
			<img class="topbanner" :src="source"></img>
			<slot name="h4"></slot>
		</div>
		<slot name="span"></slot>
	</div>
</template>
<script>
	export default{
		props: ["source"]
	}
</script>
<style scoped>
	.item{
		text-align:center;
		height: 426px;
		width: 20%;
		float: left;
		margin: 0 2.5%;
		background-color: #fff;
		box-shadow:0px 0px 30px rgba(100,100,100,0.7);
		transition: all 0.2s;
		z-index: 10;
		box-sizing: border-box;
		border: solid 1px #fff;
	}
	.item:hover{
		box-shadow:0px 0px 50px rgba(180,180,180,0.9);
		background-color: #fff;
		transform: scale(1.05,1.05);
		transition: all 0.2s;
		cursor: pointer;
		z-index: 10;
		border: solid 1px #00a0e9;
	}

	img{
		height: 100px;
		width: 100px;
		margin: 0px auto 26px;
		display: block;
	}
	h4{
		color: #333;
		font-size: 18px;
		font-weight: normal;
		padding: 0 20px;
		padding-bottom: 0px;
		margin: 0;
		line-height: 30px;
		height: 62px;
	}
	span{
		padding: 16px;
		display: block;
		color: #9e9e9e;
		line-height: 24px;
	}
	.top{
		
		height: 212px;
		margin-top: 32px;
	}
</style>