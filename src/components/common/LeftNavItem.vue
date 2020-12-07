<template>
	<div class="left-nav">
		<div class="left-search">
			<el-input placeholder="技术文章搜索" v-model="searchAc"  suffix-icon="el-icon-search"></el-input>
		</div>
		<div class="btn-show">
			<!-- <i class="el-icon-caret-right" @click="showPanel"></i> -->
			<i class="iconfont icon-zhankai" @click="showPanel"></i>
		</div>
		<div class="left-header">
			<el-row>
				<el-col :span="24">
					<div>
						<img class="left-avatar" :src="getAvatar" @click="gotoAdmin" />
					</div>
				</el-col>
			</el-row>
			<div class="left-mes">
				<p>小何</p>
			</div>
		</div>
		<div class="left-menu">
			<el-menu class="tabs-menu" background-color="#324157" active-text-color="#ffd04b" router default-active="blog">
				<el-menu-item index="/"><i class="iconfont icon-wenzhang"></i><span>首页</span></el-menu-item>
				<el-menu-item index="blog"><i class="iconfont icon-wenzhang"></i><span>技术文章</span></el-menu-item>
				<el-menu-item index="about"><i class="iconfont icon-about"></i><span>关于</span></el-menu-item>
				<el-menu-item index="comment"><i class="iconfont icon-comments"></i><span>评论</span></el-menu-item>
				<el-menu-item index="contact"><i class="iconfont icon-icon3"></i><span>联系我</span></el-menu-item>
			</el-menu>
		</div>
		<div class="left-social">
			<a href="https://github.com/hezhilong5211/blog" target="_blank"><i class="iconfont icon-github"></i></a>
			<a href="http://weibo.com/1176090144/profile?rightmod=1&wvr=6&mod=personinfo" target="_blank"><i class="iconfont icon-weibo"></i></a>
			<a href="javascript:;"><i class="iconfont icon-weixin"></i></a>
		</div>
	</div>
</template>

<script>
	export default {
		props: ['avatar'],
		data() {
			return {
				avatarRoot: '../../../static/images/avatar/',
				//技术文章搜索参数
				searchAc:''
			}
		},
		computed: {
			getAvatar() {
				return this.avatarRoot + this.avatar;
			}
		},
		methods: {
			showPanel() {
				this.$store.dispatch('changeCatalogDiaplay');
			},
			gotoAdmin() {
			  this.$http.get('/api/getSession')
					.then((res) => {
						res.data === false ? this.$router.push('/login') : this.$router.push('/admin');
					})
					.catch((err) => {
						throw err;
					})
			},
		}
	}
</script>

<style lang="scss">
	$whiteColor: #fff;
	.left-nav {
		position: fixed;
		height: 100%;
		background: #324157;
		float: left;
		color: #fff;
		text-align: center;
		overflow: auto;
	}

	.left-search {
		margin: 10px;
		cursor: pointer;
		
		input {
			background-color: transparent;
			color: $whiteColor;
		}
	}

	@media only screen and (max-width: 992px) {
		.left-nav {
			display: none;
		}
	}

	@media only screen and (min-width: 992px) {
		.left-nav {
			width: 20%;
		}
	}

	.left-header {
		position: relative;
		padding: 30px;
		.left-avatar {
			width: 30%;
			border-radius: 50%;
			cursor: pointer;
		}
	}

	.left-menu .tabs-menu {
		border: none;
		width: 100%;
		li {
			color: $whiteColor;
			&:hover {
				color: #409EFF;
			}
			i {
				padding: 0 10px;
			}
		}
		span {
			display: inline-block;
			width: 50px;
		}
	}

	.left-social {
		position: absolute;
		bottom: 0;
		padding: 10px;
		a {
			text-decoration: none
		}
		i {
			font-size: 32px;
			cursor: pointer;
			color: #fff;
			padding: 0 5px;
		}
		.icon-github:hover {
			color: #f66;
		}
		.icon-weibo:hover {
			color: #f08787;
		}
		.icon-weixin:hover {
			color: #46af35;
		}
	}

	.btn-show {
		width: 45px;
		cursor: pointer;
		margin-top: 15px;
	}
</style>
