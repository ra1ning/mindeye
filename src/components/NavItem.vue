<template>
	<div class="nav-item">
		<div class="title">{{options.title}}</div>
		<a :href="item.path" v-for="item in options.items">{{item.title}}</a>
	</div>
</template>
<script>

export default {
	props: ['options']
}
</script>
<style scoped>
.nav-item{
	float: right;
    width: 112px;
    margin-right: 8px;
    text-align: center;
    height: 50px;
    line-height: 50px;
    margin-top: 18px;
    overflow: hidden;
    transition: all 0.2s
}

.nav-item:hover{
	background-color: #303030;
	overflow: visible;
	transition: all 0.2s
}

.title,a{
	text-decoration: none;
	color: #fff;
	display: block;
	font-size: 16px;
	width: 100%;
	text-align: center;
	height: 50px;
	line-height: 50px;
}
a{
	background-color: #303030;
}
a:hover{
	background-color: #171717;
}
</style>