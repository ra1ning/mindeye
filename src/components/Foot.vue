<template>
	<div class="foot">
		<div class="wrap">
			<div class="left">
				<img :src="logoblue">
				<h1>武汉市智见科技有限公司</h1>
				<div style="margin-bottom:12px">武汉市洪山区佳园路SBI创业广场7-5-319</div>
				<div>Copyright ©2017-2017 MindSee.ai 智见版权所有 鄂公网安备 11010802020287 鄂ICP备11018762号</div>
			</div>
			<div class="right">
				<div class="sociality">
					<div style="margin-bottom:16px">
						<a href=""><img :src="weibo" style="margin-right:18px;margin-left:18px"></a>
						<a href=""><img :src="wechat"></a>
					</div>
					<img :src="QRcode">
				</div>
				<div class="contact">
					<div style="font-size:24px;margin-bottom:10px">联系方式</div>
					<div>联系邮箱：<img class="icon" :src="email"><a href="mailto:yanyi@mindeye.ai">yanyi@mindeye.ai</a></div>
					<div>公司电话：<img class="icon" :src="phone">02782285513</div>
					<div>公司网址：<img class="icon" :src="net"><a href="http://www.mindeye.ai">http://www.mindeye.ai</a></div>
				</div>
			</div>
		</div>
	</div>
</template>
<script>
	import logoblue from '../assets/logoblue.png'
	import weibo from '../assets/weibo.png'
	import wechat from '../assets/wechat.png'
	import phone from '../assets/phone.png'
	import net from '../assets/net.png'
	import email from '../assets/email.png'
	import QRcode from '../assets/QRcode.png'

	export default{
		data(){
			return {
				logoblue: logoblue,
				weibo: weibo,
				wechat: wechat,
				phone: phone,
				net: net,
				email: email,
				QRcode: QRcode
			}
		}
	}
</script>
<style scoped>
	.wrap{
		height: 100%;
		max-width: 1366px;
		margin: 0 auto;
	}
	h1{
		font-size: 24px;
		font-weight: 500;
		margin-bottom: 52px;
		margin-top:0;
	}
	.foot{
		color: #fff;
		background-color: #1a2227;
		overflow: hidden;
		padding-left: 62px;
		padding-right: 62px;
		padding-bottom: 24px;
		box-sizing: border-box;
		width: 100%;
	}
	.left{
		float: left;
		text-align: left;
	}
	.left div{
		font-size: 14px;
		color: #fff;
	}
	.left img{
		margin-top: 80px;
		margin-bottom: 42px;
	}
	.right{
		padding-top: 150px;
		float: right;
		text-align: left;
		
		font-size: 18px;
		
	}
	a{
		color: #fff;
		text-decoration: none;
	}
	.sociality{
		width: 130px;
		margin-right: 24px;
	}
	.sociality div img{
		width: 40px;
	}
	.contact,.sociality{
		float: left;

	}
	.icon{
		width: 22px;
		height: 22px;
		margin-right: 10px;
		vertical-align: middle;
	}
	.contact{
		line-height: 46px;
	}
    
	@media screen and (max-width: 1280px) {
		.right{
		  float: left!important;
		}
	}
	@media screen and (max-width: 430px) {
		.contact{
			font-size: 14px;
			line-height: 28px;
			margin-top: 20px;
		}
		.foot{
			padding: 20px;
		}
		.right{
			padding-top: 50px;
		}
		h1{
			font-size: 18px;
			margin-bottom: 20px;
		}
		.left img{
			margin-top: 40px;
			margin-bottom: 20px;
		}
	}
</style>