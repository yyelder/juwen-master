<template>
	<div ref='root' class="wish-page">
		<img :src='background' />
		<component v-for="(item, index) in items" :is="item.name" :key="index" :left="item.left" :top="item.top" :width="item.width"
		 :value="item.value" :height="item.height" :placeholder="item.placeholder" :submit="item.submit" :items="item.items"
		 :src="item.src" @click="item.submit ? post() : $emit(item.event)">
		</component>
	</div>
</template>

<script>
	import WishList from '../components/List.vue'
	import WishInput from '../components/Input.vue'
	import WishButton from '../components/Button.vue'
	import WishUpload from '../components/Upload.vue'
	import WishCheckbox from '../components/CheckBox.vue'

	export default {
		name: 'wish-page',
		props: ['items', 'index', 'msg', 'background'],
		components: {
			WishList,
			WishInput,
			WishButton,
			WishUpload,
			WishCheckbox
		},
		methods: {
			// 提交当前页面
			post() {
				if (this.valid())
					this.$emit('submit');
				else
					this.error();
			},
			// 提示错误
			error() {
				if (this.msg)
					alert(this.msg);
			},
			// 检验各项数据是否填写正确
			valid() {
				for (let item in this.$children) {
					var component = this.$children[item];
					console.log(component);
					if (component.test && !component.valid())
						return false;
				}
				return true;
			},
			show() {
				this.$refs['root'].style.display = "block";
			},
			hide() {
				this.$refs['root'].style.display = "none";
			}
		}
	}
</script>

<style scoped>
	.wish-page {
		display: none;
		position: absolute;
		left: 0px;
		top: 0px;
		width: 100%;
		height: 100%;
	}

	.wish-page img {
		display: block;
		-ms-user-select: none;
		-moz-user-select: none;
		-ms-touch-select: none;
		-webkit-user-select: none;
	}
</style>
