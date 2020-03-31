<template>
	<header class="login-header">
		<h1>辽宁省交通运输厅综合管理系统</h1>
		<div class="routers">
			<a href="javascript:;" class="active">首页</a>
			<span>|</span>
			<a href="javascript:;">应用系统</a>
			<span>|</span>
			<a href="javascript:;">
				<span class="el-icon-menu"></span>
				<span>更多</span>
			</a>
		</div>
		<div class="header-right-bar">
			<div class="user-info">
				<span class="name">欢迎XXX，登录辽宁省交通运输厅综合管理系统</span>
				<span class="line">|</span>
				<a href="javascript:;">一键登出</a>
			</div>
			<div class="search-bar">
			  <el-input placeholder="请输入内容" v-model="input3" class="input-with-select">
				<el-button slot="append" icon="el-icon-search"></el-button>
			  </el-input>
			</div>
		</div>
	</header>
</template>

<script>
</script>

<style lang="less">
	.login-header {
		width: 100%;
		height: 150px !important;
		border-bottom: 2px solid #4185c7;
		background: url(../assets/images/header-bg.png) no-repeat center;
		background-size: cover;
		display: flex;
		align-items: center;
		padding:0 40px;
		box-sizing: border-box;
	
		h1 {
			width: 639px;
			height: 104px;
			padding-left: 100px;
			background: url(../assets/images/guohui.png) no-repeat left center;
			line-height: 104px;
			font-size: 40px;
			font-family: "Adobe Heiti Std";
			color: #535455;
			line-height: 104px;
			text-align: left;
			margin: 0;
		}
		.routers{
			>a{
				color: #555555;
				text-decoration: none;
				font-size: 21px;
				span{
					color: #888888;
					
				}
			}
			a.active{
				color: #4185c7;
			}
			>span{
				margin:0 20px;
			}
			span{
				color: #adc8dd;
			}
		}
		.header-right-bar{
			flex:1;
			text-align: right;
			position: relative;
			top:-20px;
			.user-info{
				font-size: 16px;
				color: #666666;
				margin-bottom:15px;
				.line{
					margin:0 20px;
					color: #a2bacc;
				}
				a{
					color: #4185c7;
					text-decoration: none;;
				}
			}
			.search-bar{
				width: 325px;
				text-align: rigth;
				float: right;
				.el-input-group__append{
					background-color: #4185c7;
					color: #fff;
					font-weight: bolder;
					font-size: 18px;
					border-color: #4185c7;
				}
			}
		}
	}
	
</style>
