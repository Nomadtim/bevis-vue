<!-- 使用 lang="scss" 或者其他预编译直接可以使用 -->
<!-- 添加 "scoped" 参数可以限制这个css央视只在这个模块使用 -->
<style lang="scss" scoped>
	@import '../assets/css/appHeader.scss';
</style>

<template>
	<div id="header">
		<div class="hd_bar">
			<div class="bd_bar_bd cle">
				<ul class="welcome">
					<li>
						<a href="html/user_login.html">请登录</a>
						<s>|</s>
						<a href="html/register.html">免费注册</a>
					</li>
				</ul>
				<ul id="userinfo-bar">
					<li class="more-menu">
						<a href="">我的海贼团</a>
						<i class="iconfont icon-arrow"></i>
						<div class="more-bd">
							<div class="list">
								<!-- v-for 指令基于一个数组渲染一个列表 -->
								<a href="" v-for="mine in mines">{{mine.name}}</a>
							</div>
						</div>
					</li>
					<li class="more-menu" id="header_guanzhu">
						<a class="menu-link" href="https://github.com/utopia1991" target="_blank">关注我吧</a>
					</li>
				</ul>
			</div>
		</div>
		<div class="hd_main cle">
			<div class="logo">
				<p>
					<a href=""class="lizi_logo"></a>
				</p>
			</div>
			<div class="search_box">
				<form>
					<input class="sea_input" type="text" name="keywords" id="keyword" value="" autocomplete="off">
					<input type="hidden" value="k1" name="dataBi">
					<button type="button" class="sea_submit" id="search">上船</button>
				</form>
			</div>
			<div class="head_search_hot">
				<span>热搜榜：</span>
				<!-- 我们可以传给 v-bind:class 一个对象，以动态地切换 class。注意 v-bind:class 指令可以与普通的 class 特性共存 -->
				<!-- 双 Mustache 标签( {{}} )将数据解析为纯文本而不是 HTML。为了输出真的 HTML 字符串，需要用三 Mustache 标签： <div>{{{ raw_html }}}</div> -->
				<a v-for="good in goods" v-bind:href="good.url" target="_blank">{{good.name}}</a>
			</div>
			<div class="intro">
				<h2>
					<a href="https://utopia1991.github.io/" target="_blank">{{blogName}}</a>
				</h2>
				<p>
					{{subTitle}}
					<em class="favor-account">+{{favorAccountPlus}}</em>
				</p>
			</div>
		</div>
		<nav class="hd_nav">
			<div class="hd_nav_bd cle">
				<div class="main_nav" id="main_nav">
					<div class="main_nav_link">
						<a href="html/allCategory.html"	target="_blank">路飞海贼团人员</a>
						<i class="iconfont icon-arrow"></i>
					</div>
					<div class="main_cata" id="J_mainCata" style="opacity: 0; display: none;">
						<ul>
							<li class="first" v-for="tab in tabs">
								<h3>
									<a target="_blank" :href="tab.url">{{tab.name}}</a>
								</h3>
							</li>
						</ul>
					</div>
				</div>
				<ul class="sub_nav cle" id="sub_nav">
					<!-- 我们可以传给 v-bind:class 一个对象，以动态地切换 class。注意 v-bind:class 指令可以与普通的 class 特性共存 -->
					<li v-for="tab in tabs" v-bind:class="{ current:tab.isActive }">
						<a :href="tab.url">{{tab.name}}</a>
					</li>
				</ul>
			</div>
		</nav>
	</div>
</template>

<script>
export default {
	data () {
		return {
			blogName: 'Welcome To Bevis\'s Blog',
			subTitle: 'Bevis Shen',
			favorAccount: 8888,
			goods: [
				{
					url: 'https://router.vuejs.org/zh-cn/index.html',
					name: '路飞'
				},
				{
					url: 'http://vuex.vuejs.org/',
					name: '索隆'
				},
				{
					url: 'http://vue-loader.vuejs.org/',
					name: '山治'
				},
				{
					url: 'https://github.com/vuejs/awesome-vue',
					name: '娜美'
				},
				{
					url: 'https://github.com/vuejs/awesome-vue',
					name: '乌索普'
				}
			],
			mines: [
				{
					name: '我的订单'
				},
				{
					name: '我的评价'
				},
				{
					name: '我的余额'
				},
				{
					name: '我的红包'
				},
				{
					name: '我的收藏'
				},
				{
					name: '修改收货地址'
				}
			],
			tabs: [
				{
					url: '/index',
					isActive: true,
					name: '首页'
				},
				{
					url: '/luffy',
					name: '路飞'
				},
				{
					url: '/zero',
					name: '索隆'
				},
				{
					url: '/sanji',
					name: '山治'
				},
				{
					url: '/nami',
					name: '娜美'
				},
				{
					url: '/usopp',
					name: '乌索普'
				},
				{
					url: '/chopper',
					name: '乔巴'
				},
				{
					url: '/robin',
					name: '罗宾'
				},
				{
					url: '/frank',
					name: '弗兰克'
				},
				{
					url: '/brook',
					name: '布鲁克'
				}
			]
		}
	},
	computed: {
		// 一个计算属性的 getter
		favorAccountPlus: function () {
			// `this` 指向 vm 实例
			return this.favorAccount + 1111
		}
	},
	methods: {
		// ps:在vue里字符串被规定位要用单引号,且注释的时候双斜杆后面要用空格
	}
}
</script>
