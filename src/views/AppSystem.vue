<template>
	<div class="as-container">
		<headerComs />
		<div class="as-content">
			<el-breadcrumb separator-class="el-icon-arrow-right" class="breadcrumb">
			  <el-breadcrumb-item :to="{ path: '/' }">首页</el-breadcrumb-item>
			  <el-breadcrumb-item>应用系统列表</el-breadcrumb-item>
			</el-breadcrumb>
			<div class="as-content-body">
				<div class="as-item-box left-box">
					<div class="item-header">
						<div class="title">常用系统</div>
					</div>
					<div class="c-item-contetn">
					<div class="item-b" v-for="(item,i) in leftItems" key="i" :class="{'active':currentIndex==i}" @click="currentIndex=i">
						<span class="icon"></span>
						<span class="title">{{item}}</span>
					</div>
					</div>
				</div>
				<div class="as-item-box right-box">
					<div class="item-header">
						<div class="title">常用系统</div>
					</div>
					<div class="c-item-contetn">
				
					</div>
				</div>
			</div>
		</div>
		<footerComs />
	</div>
</template>

<script>
	// @ is an alias to /src
	import headerComs from '../components/header_coms.vue'
	import footerComs from '../components/footer_coms.vue'
	export default {
		name: 'as',
		data() {
			return {
				currentIndex:1,
				leftItems:[
					'常用系统',
					'政务办公服务',
					'辅助决策支持',
					'综合行政执法',
					'路网运行监测',
					'应急指挥调度',
					'安全生产监管',
					'综合信用管理',
					'网络安全保障'


				]
			}
		},
		components: {
			headerComs,
			footerComs
		}
	}
</script>
<style lang="less">
	.as-container {
		display: flex;
		flex-direction: column;
		align-items: center;

		.as-content {
			width: 1200px;
			display: flex;
			flex-wrap: wrap;
			// justify-content: space-between;
			min-height: ~'calc(100vh - 210px)';
			box-sizing: border-box;
			flex-direction: column;
			.breadcrumb{
				height: 40px;
				line-height: 40px;
			}
			.as-content-body{
				display: flex;
				justify-content: space-between;
			}
		}
	}
	
	.as-item-box {
		width: 587px;
		border: 1px solid #eeeeee;
		border-top: 1px solid #4185c7;
		margin-bottom: 20px;

		.item-header {
			height: 40px;
			background-color: #eff7ff;
			display: flex;
			justify-content: space-between;
			align-items: center;
			padding: 0 20px;
			;

			.title {
				font-size: 16px;
				color: #202426;
				position: relative;
				text-indent: 10px;
				;

				&::after {
					position: absolute;
					content: '';
					height: 16px;
					width: 3px;
					background-color: #4185c7;
					left: 0;
					top: 12px;
					margin-top: -8px;
				}
			}

			.op {
				color: #8c8c8c;
				font-size: 14px;
				span{
					margin:0 10px;
				}
			}
		}

		.c-item-contetn {
			padding: 20px;
		}

	}
	.as-item-box.left-box{
		width: 280px;
		.c-item-contetn {
			padding: 10px 0px;
		}
		.item-b{
			height: 42px;
			line-height: 42px;;
			font-size: 18px;
			color: #202426;
			cursor: pointer;
			&.active,
			&:hover{
				background: url(../assets/images/as-left-bg.png) no-repeat center;
				background-size: cover;
				color: #fff;;
			}
		}
	}
	.as-item-box.right-box{
		width: 900px;
	}
</style>
