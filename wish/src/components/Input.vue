<template>
	<div ref='root' class="wish-page-components">
		<input ref='input' :placeholder='placeholder' />
	</div>
</template>

<script>
	import WishBaseComponent from './BaseComponent.vue'
	export default {
		extends: WishBaseComponent,
		name: 'wish-input',
		props: ['placeholder'],
		created() {
			this.test = true;
		},
		methods: {
			valid() {
				return this.value == this.$refs['input'].value;
			}
		}
	}
</script>

<style scoped>
	input {
		width: 100%;
		height: 100%;
		border: none;
		font-size: 16px;
		font-family: '微软雅黑';
	}
</style>
