<template>
	<div ref='root' class="wish-page-components">
		<label class="ci-check-lable">
			<input ref='checkbox' type="checkbox" />
		</label>
	</div>
</template>

<script>
	import WishBaseComponent from './BaseComponent.vue'
	export default {
		extends: WishBaseComponent,
		name: 'wish-checkbox',
		created() {
			this.test = true;
		},
		methods: {
			valid() {
				return this.$refs['checkbox'].checked;
			}
		}
	}
</script>

<style scoped>
	label {
		position: absolute;
		top: 0px;
		left: 0px;
		width: 100%;
		height: 100%;
		font-size: 16px;
		font-family: '微软雅黑';
	}
	label input{
		position: absolute;
		top: 0px;
		left: 0px;
	}
</style>
