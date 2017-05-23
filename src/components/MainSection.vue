<template>
		<div class="main">
			<MainItem :source="i1">
				<h4 slot="h4">DCC EYE 智慧城市交通辅助系统</h4>
				<span slot="span">为城市交通提供基于移动视频的城市管理辅助系统，可有效补充城市固定监控无法覆盖的区域的交通实时状况监测。</span>
			</MainItem>
			<MainItem :source="i2">
				<h4 slot="h4">ADAS辅助驾驶系统</h4>
				<span slot="span">为汽车提供高精确度的驾驶安全算法，为前装市场、后装市场设计专门的算法模型，为车载智能硬件提供ADAS SDK，在各种硬件平台上实现精确的ADAS功能。</span>
			</MainItem>
			<MainItem :source="i3">
				<h4 slot="h4">FACE CODE 面部微表情识别系统</h4>
				<span slot="span">基于深度学习的卷积神经网络为疲劳检测及面部表情分析提供基于心理分析的面部表情识别系统，在微表情识别率上达到目前该领域的最高识别效果。</span>
			</MainItem>
			<MainItem :source="i4">
				<h4 slot="h4">汽车后市场服务网络</h4>
				<span slot="span">遍布湖北、江西、重庆、四川近千家汽车后服务网点，为银联、农行、华夏银行等金融机构、人保、平安等保险机构提供后市场汽车服务。</span>
			</MainItem>	
		</div>
</template>
<script>
	import MainItem from "./MainItem"
	import i1 from '../assets/city_traffic.png'
	import i2 from '../assets/drive_assistance.png'
	import i3 from '../assets/micro_expression.png'
	import i4 from '../assets/car_service.png'
	export default{
		components: { MainItem },
		data(){
			return {
				i1: i1,
				i2: i2,
				i3: i3,
				i4: i4
			}
		}
	}
</script>
<style scoped>
	.main{
		background-color: #fff;
		max-width: 1366px;
		padding:20px;
		margin: 0 auto
	}
	.main:after{
		content: "";
		display: block;
		clear: both;
	}
</style>