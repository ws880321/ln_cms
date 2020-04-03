<template>
	<el-container class='login-container'>
		<el-header class="lobin-header">
			<h1>辽宁省交通运输厅综合管理系统</h1>
		</el-header>
		<el-main class="login-main">
			
			<el-tabs type="card" class="box2 login-form-wrap">
				<el-tab-pane label="账号密码登陆">
					<el-form :model="ruleForm"  ref="ruleForm" label-width="60px" class="login-form">
						<h3 class="form-head"><span>账号登陆</span></h3>
						<el-form-item label="账号" prop="name">
							<el-input v-model="ruleForm.name"></el-input>
						</el-form-item>
						<el-form-item label="密码" prop="password">
							<el-input type="password" v-model="ruleForm.password" autocomplete="off"></el-input>
						</el-form-item>
						<el-form-item>
							<el-button type="primary" class="sub-btn" @click="submitForm('ruleForm')" >立即登陆</el-button>
						</el-form-item>
						<el-form-item class="form-tips">
							<span><i v-loading="loading"></i>本地证书检测中...</span>
							<a href="javascript:;">证书下载</a>
						</el-form-item>
						
					</el-form>
				</el-tab-pane>
				<el-tab-pane label="扫码登陆">
				<el-form  label-width="60px" class="login-form">
						<h3 class="form-head"><span>扫码登陆</span></h3>
						<div class="ercode">
							<img src="../assets/images/ercode.gif">
						</div>
						<p>扫一扫登陆</p>
						
						
					</el-form></el-tab-pane>
			</el-tabs>
			
		</el-main>
		<footerComs/>
	</el-container>
</template>

<script>
	// 引入公共底部组件
	import footerComs from '../components/footer_coms.vue'
  export default {
    data() {
      return {
        ruleForm: {
          name: '',
          password: '',
        },
		loading:true,
		// 登陆验证规则
        rules: {
          name: [
            { required: true, message: '请输入账号', trigger: 'blur' },
            { min: 3, max: 5, message: '长度在 3 到 5 个字符', trigger: 'blur' }
          ],
		  password: [
		    { required: true, message: '请输入密码', trigger: 'blur' },
		    { min: 3, max: 5, message: '长度在 3 到 5 个字符', trigger: 'blur' }
		  ]
        }
      };
    },
	components:{footerComs},
    methods: {
	  // 登陆提交事件
      submitForm(formName) {
		 this.$router.push('/home')
        this.$refs[formName].validate((valid) => {
          if (valid) {
            // alert('submit!');
          } else {
            console.log('error submit!!');
            return false;
          }
        });
      },
      resetForm(formName) {
        this.$refs[formName].resetFields();
      }
    }
  }
</script>
<style lang="less" scoped>
	.login-container {
		display: flex;
		flex-direction: column;
		width: 100%;
		height: 100vh;
	}

	.lobin-header {
		width: 100%;
		height: 150px !important;
		border-bottom: 2px solid #4185c7;
		background: url(../assets/images/header-bg.png) no-repeat center;
		background-size: cover;
		display: flex;
		align-items: center;

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
			text-shadow: -2px -3px 5px #fff;
		}
	}

	.login-main {
		width: 100%;
		flex: 1;
		background: url(../assets/images/login-main-bg.png) no-repeat left center;
		background-size: contain;
		position: relative;
		background-color: #f9f9f9;
		.login-form-wrap{
			background-color: #fff;
			border-top: 2px solid #4185c7;
			position: absolute;
			height: 400px;
			width: 430px;
			right: 130px;
			margin-top: -220px;
			top: 50%;
			box-shadow: 0 0 12px 5px #eeeeee;
			box-sizing: border-box;
			.el-tabs__nav{
				display: flex!important;
				width:100%;
				background-color: #eff7ff;
				text-align:center;

				.el-tabs__item{
					flex:1!important;
					display: flex!important;
					align-items:center!important;
					text-align:center!important;
					justify-content:center!important;
					&.is-active{
						background-color: #fff;
					}
				}
			}
		}
		.login-form {
			background-color: #fff;
			height: 400px;
			width: 430px;
			right: 130px;
			padding: 5px 30px;
			box-sizing: border-box;
			p{
				text-align: center;
				color: #555;
			}
		}
		.ercode{
			width: 200px;
			height: 200px;
			margin:0 auto;
			border:1px solid #eee;
			padding:3px;
			img{
				width:100%;
				height: 100%
			}
		}
	}
	.form-tips{
		position: relative;
		top:-10px;
		.el-form-item__content{
			width: 100%;
			display: flex;
			align-items: center;
			justify-content: space-between;
			margin-left:0!important;
			padding-left:60px;
			box-sizing: border-box;
			&::after{
				position: absolute;
			}
			&::before{
				position: absolute;
			}
			span{
				display: flex;
				align-items: center;
				justify-content: space-between;
				font-size: 14px;
				color: #4185c7;
			}
			a{
				color: #999999;
				font-size: 14px;;
			}
		}
	}
	.form-tips i{
		display: inline-block;
		position: relative;
		width: 30px;
		height: 30px;
		.el-loading-mask{
			transform: scale(0.5);
		}
	}
	.sub-btn{
		background-color: #4185c7;
		width: 100%;;
	}
	.login-footer {
		width: 100%;
		height: 60px;
		background-color: #f6f6f6;
		display: flex;
		align-items: center;
		justify-content: center;
		border-top:1px solid #e6e6e6;

		span {
			margin: 0 10px;
			font-size: 14px;
			color: #555555;
		}
	}
	.form-head{
		position: relative;
		text-align: left;;
		font-size: 20px;
		color: #202426;
		font-weight: normal;
		margin-bottom:35px;
		span{
			position: relative;
			z-index: 20;
		}
	}
	.form-head::after{
			content: '';
			width: 84px;
			height: 12px;
			background-color: #d9e7f490;
			position: absolute;
			left:-2px;
			bottom:3px;
			
	}
	
</style>

