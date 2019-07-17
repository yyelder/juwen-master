<template>
	<div ref='root' class="wish-task">
		<wish-page :ref="'page'+index" v-for="index in 5" :key="index" :index="index" :background='require("../assets/task2/background/" + index + ".jpg")'
		 :items="require('../assets/task2/json/' + index + '.json')" @submit="submitHandler(index)" msg="填写错误" @SendCode="sendCodeHandler(index)">
		</wish-page>
		<button style="left: 100px" @click="prev">上一页</button>
		<button style="left: 220px" ref="page-index">当前页：0</button>
		<button style="left: 350px" @click="next">下一页</button>
	</div>
</template>

<script>
	import WishPage from '../views/Page.vue'

	export default {
		name: 'wish-task2',
		components: {
			WishPage
		},
		data() {
			return {
				current: 0
			}
		},
		methods: {
			// 跳转页面（关闭当前，并打开新页面）
			to(index) {
				if (index < 1 || index > 5)
					return;
				console.log("try to page" + index + "!")
				if (this.page(this.current))
					this.page(this.current).hide();
				this.current = index;
				this.$refs["page-index"].innerHTML = "当前页：" + index;
				if (this.page(this.current))
					this.page(this.current).show();
			},
			// 打开页面
			open(index) {
				if (this.page(index))
					this.page(index).show();
			},
			// 关闭页面
			close(index) {
				if (this.page(index))
					this.page(index).hide();
			},
			// 获取页面组件
			page(index) {
				if (this.$refs['page' + index])
					return this.$refs['page' + index][0];
				else
					return null;
			},
			prev() {
				this.to(this.current - 1);
			},
			next() {
				this.to(this.current + 1);
			},
			// 处理提交事件
			submitHandler(index) {
				console.log("page" + index + " submit!");
				if (index == 3) {
					this.close(3);
				} else if (index == 2) {
					this.to(4);
				} else {
					this.to(index + 1);
				}
			},
			// 提交二维码事件
			sendCodeHandler(index) {
				if (index == 2)
					this.open(3);
			}
		},
		mounted() {
			// 第七页添加省市下拉框
			this.$refs["page7"];
			// 跳转第一页
			this.to(1);
		}
	}
</script>

<style scoped>
	button {
		position: fixed;
		z-index: 1000;
		width: 100px;
		height: 50px;
	}
</style>
