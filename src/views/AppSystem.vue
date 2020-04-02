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
					<div class="item-b" v-for="(item,i) in leftItems" :key="i" :class="{'active':currentIndex==i }" @click="currentIndex=i">
						<span class="iconfont " :class="item.class"></span>
						<span class="title">{{item.title}}</span>
					</div>
					
					</div>
				</div>
				<div class="as-item-box right-box box3">
					<div class="item-header">
						<div class="title">常用系统</div>
						<div class="op">
							<span @click="edit=true" v-if="!edit"><i class="el-icon-plus"></i>添加到首页</span>
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
						</ul>
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
				edit:false,
				currentArray:[],
				currentIndex:1,
				leftItems:[
					{
						class:'icon_changyong',
						title:'常用系统'
					},
					{
						class:'icon_zhengwu',
						title:'政务办公服务'
					},
					{
						class:'icon_fuzhujuece',
						title:'辅助决策支持'
					},
					{
						class:'icon_anquanzhifa',
						title:'综合行政执法'
					},
					{
						class:'icon_luwang',
						title:"路网运行监测"
					},
					{
						class:'icon_gaojing',
						title:"应急指挥调度"
					},
					{
						class:'icon_anquan',
						title:"安全生产监管"
					},
					{
						class:'icon_xinyong',
						title:"综合信用管理"
					},
					{
						class:'icon_wangluo',
						title:"网络安全保障"
					},
				],//list1  为常用系统 模块信息
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
					},{
						id:8,
						name:'OA系统'
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
				let newlist=[]
				if(this.currentArray.length){
					this.currentArray.forEach(v=>{
						this.list1.forEach(k=>{
							// if(k.id!=){}
						})
					})
				}
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
				i{
					margin:0 8px;
				}
				.ok-btn{
					color:  #4185c7;;
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
			text-align: center;
			color: #202426;
			cursor:pointer;
			display: flex;
			align-items: center;
			justify-content: center;
			margin-bottom:5px;
			&.active,
			&:hover{
				background: url(../assets/images/as-left-bg.png) no-repeat center;
				background-size: cover;
				color: #fff;
				.iconfont{
					color: #fff;;
				}
			}
			.iconfont{
				font-size: 22px;
				color: #4185c7;;
			}
			.title{
				display: inline-block;;
				width: 150px;
				text-align: center;
			}
			
		}
	}
	.as-item-box.right-box{
		width: 900px;
	}
</style>
<style lang="scss">
	
</style>
