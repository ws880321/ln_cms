<template>
	<div class="home-container">
		<headerComs />
		<div class="home-content">
			<div class="c-item-box">
				<div class="item-header">
					<div class="title">通知公告</div>
					<div class="op">更多》</div>
				</div>
				<div class="c-item-contetn box1">
					<div class="img-new">
						<img src="../assets/images/p.png" alt="">
						<h4 class="title">省交通运输厅召开全省交通运输安全生产工作会议</h4>
						<p>2020-03-22</p>
					</div>
					<ul class="list">
						<li v-for="(item,i) in list0" :key="i">
							<p>{{item.title}}</p>
							<span>{{item.time}}</span>
							
						</li>
					
					</ul>
				</div>
			</div>
			<div class="c-item-box box2-wrap ul-list">
				<el-tabs type="card" class="box2">
					<el-tab-pane label="待办">
						<ul>
							<li v-for="i in 5" :key="i">
								<p>
									<span>您有一条新的待办信息，请立即处理。</span>
									<span class="source">来源系统：辽宁省汽车客运互联网售票系统</span >
								</p>
								<a href="javascript:;">查看</a>
							</li>
							
						</ul>
					</el-tab-pane>
					<el-tab-pane label="待阅">待阅</el-tab-pane>
				</el-tabs>
				<div class="op2">更多》</div>
			</div>
			<div class="c-item-box box3">
				<div class="item-header">
					<div class="title">常用系统</div>
					<div class="op">
						<span @click="edit=true" v-if="!edit"><i class="el-icon-edit"></i>管理</span>
						<span  v-if="!edit">更多》</span>
						<span class="cancel-btn"  v-if="edit" @click="edit=false">取消</span>
						<span class="ok-btn"  v-if="edit" @click="submit">确定</span>
					</div>
				</div>
				<div class="c-item-contetn">
					<ul>
						<li v-for="(item,i) in list1" :key="i">
							<span class="radio" v-if="edit" :class="{'active':hasC(item.id)}" @click="addC(i)"></span>
							<span class="icon"></span>
							<p>{{item.name}}</p>
						</li>
						<li><span class="icon add-icon"><i class="el-icon-plus"></i></span></li>
					</ul>
				</div>
			</div>
			<div class="c-item-box ul-list">
				<div class="item-header">
					<div class="title">新消息提醒</div>
					<div class="op">更多》</div>
				</div>
				<div class="c-item-contetn">
					<ul>
						<li v-for="i in 5" :key="i">
							<span>您有一条新的待办信息，请立即处理。</span>
							<a href="javascript:;">查看</a>
						</li>
					</ul>
				</div>
			</div>
		</div>
		<footerComs />
	</div>
</template>

<script>
	// 引入公共头部组件
	import headerComs from '../components/header_coms.vue'
	// 引入公共底部组件
	import footerComs from '../components/footer_coms.vue'
	export default {
		name: 'Home',
		data() {
			return {
				edit:false,
				currentArray:[],
				//list0  为通知公告 模块信息
				list0: [
					{
						title:'辽宁省交通运输行政综合管理系统门户统一平台升级改造完成',
						time:'20200-030-30'
					},{
						title:'辽宁省交通运输行政综合管理系统门户统一平台升级改造完成',
						time:'20200-030-30'
					},{
						title:'辽宁省交通运输行政综合管理系统门户统一平台升级改造完成',
						time:'20200-030-30'
					},{
						title:'辽宁省交通运输行政综合管理系统门户统一平台升级改造完成',
						time:'20200-030-30'
					},{
						title:'辽宁省交通运输行政综合管理系统门户统一平台升级改造完成',
						time:'20200-030-30'
					}
					
				],
				
				//list1  为常用系统 模块信息
				list1: [
					{
						id:0,
						name:'辽宁省交通厅公路管理局普通公路沥青运输车辆监管服务平台'
					},
					{
						id:1,
						name:'辽宁省交通工程质量与安全监督综合信息系统'
					},
					{
						id:2,
						name:'辽宁省汽车客运互联网售票系统'
					},
					{
						id:3,
						name:'重点营运车辆卫星定位行业监督考核系统'
					},
					{
						id:4,
						name:'辽宁省公路沥青拌和站远程实时监控系统'
					},
					{
						id:5,
						name:'辽宁省普通公路桥隧管理系统'
					},
					{
						id:6,
						name:'辽宁省危险货物港口作业安全监管信息管理系统'
					},{
						id:7,
						name:'基于GIS的辽宁省港口资源管理及应用指挥系统'
					},
				]
			}
		},
		methods:{
			hasC(i){
				 return this.currentArray.indexOf(i)>=0
			},
			addC(i){
				let index=this.currentArray.indexOf(i)
				if(index==-1){
					this.currentArray.push(i)
				}else{
					this.currentArray.splice(index,1)
				}
			},
			submit(){
				this.edit=false
				//请求后台数据更新 list1
			}
		},
		components: {
			headerComs,
			footerComs
		}
	}
</script>
<style lang="less">
	.home-container {
		display: flex;
		flex-direction: column;
		align-items: center;

		.home-content {
			width: 1200px;
			padding: 25px 0;
			display: flex;
			flex-wrap: wrap;
			justify-content: space-between;
			min-height: ~'calc(100vh - 210px)';
			box-sizing: border-box;
		}
	}

	.c-item-box {
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
					cursor: pointer;
				}
				.ok-btn{
					color:  #4185c7;;
				}
			}
		}

		.c-item-contetn {
			padding: 20px;
		}

		.box1 {
			display: flex;

			.img-new {
				width: 279px;
				display: flex;
				flex-direction: column;
				align-items: flex-start;
				text-align: left;
				padding-top: 17px;

				img {
					width: 279px;
					height: 168px;
				}

				h4 {
					margin: 10px 0;
					font-size: 14px;
					font-weight: normal;
					color:#444444;
				}

				p {
					margin: 0px 0;
					color: #8c8c8c;
					font-size: 14px;;
				}
			}

			ul {
				margin: 0;
				padding: 0;
				margin-left: 20px;
			}

			li {
				list-style: none;
				position: relative;
				font-size: 14px;
				text-align: left;
				color: #555555;
				background-color: #fcfcfc;
				border-bottom: 1px solid #eeeeee;
				line-height: 20px;
				display: flex;
				align-items: center;

				p {
					margin: 10px 0;
				}

				span {
					position: absolute;
					right: 5px;
					bottom: 10px;
					color: #999999;
				}
			}
		}

		.box2 .el-tabs__header {
			background-color: #eff7ff;
		}

		.box2 .el-tabs__nav {
			border: none !important;
		}

		.box2 .is-active {
			background-color: #fff !important;
			border: none;
		}

		.box2 ul {
			padding: 0 20px;
			li {
				
				height: 40px;
				p{
					max-width: 500px;
					display: flex;
					flex-direction: column;
					justify-content: center;
					margin:0;
					line-height: 20px;
					cursor: pointer;
					span.source{
						font-size: 12px;
						color: #8c8c8c;
						
					}
				}
			}
		}



	}

	.box2-wrap {
		position: relative;

		.op2 {
			position: absolute;
			right: 20px;
			top: 10px;
			z-index: 100;
			color: #8c8c8c;
				font-size: 14px;
		}
	}

	.ul-list {
		ul {
			margin: 0;
			padding: 0;
		}

		li {
			list-style: none;
			display: flex;
			justify-content: space-between;
			margin: 0;
			height: 40px;
			line-height: 40px;
			font-size: 14px;
			color: #555555;
			margin-bottom: 20px;
			align-items: center;

			a {
				border: 1px solid #a8c7e5;
				color: #a8c7e5;
				border-radius: 15px;
				padding: 0 20px;
				height: 30px;;
				display: flex;
				text-decoration: none;
				align-items: center;
			}
		}
	}

	.box3 {
		ul {
			margin: 0;
			padding: 0;
			display: flex;
			flex-wrap: wrap;
			justify-content: space-between;

			li {
				list-style: none;
				display: flex;
				width: 270px;
				align-items: center;
				margin-bottom: 20px;
				position: relative;
				.radio{
					width: 18px;height: 18px;
					border:1px solid #4185c7;
					border-radius: 50%;
					background-color: #fff;
					box-sizing: border-box;
					position: absolute;
					top:-9px;
					left:-9px;
					&.active{
						background:url(../assets/images/right.png) no-repeat center #fff;
					}
				}
				.icon {
					display: inline-block;
					height: 44px;
					width: 44px;
					background: url(../assets/images/car.png) no-repeat center #f4f5f7;
					border: 1px solid #e3ecf2;
					border-radius: 3px;
					;
				}

				;

				.add-icon {
					background-image: none;
					display: flex;
					align-items: center;
					justify-content: center;
					font-size: 20px;
					color: #4185c7;
				}

				p {
					flex: 1;
					line-height: 16px;
					text-align: left;
					font-size: 14px;
					margin: 0;
					margin-left: 15px;
					color: #555555;
					;
				}
			}
		}
	}
</style>
