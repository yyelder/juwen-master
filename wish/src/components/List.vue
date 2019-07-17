<template>
	<div ref='root' class="wish-page-components">
		<select @change="$emit('change')" ref='select'>
			<option v-for="item in items" :key="item.id" :value="item">
				{{ item }}
			</option>
		</select>
	</div>
</template>

<script>
	import WishBaseComponent from './BaseComponent.vue'
	export default {
		extends: WishBaseComponent,
		name: 'wish-list',
		props: {
			items: Array
		},
		created() {
			this.test = true;
		},
		methods: {
			valid() {
				return this.value == this.$refs['select'].value;
			}
		}
	}
</script>

<style scoped>
	select {
		width: 100%;
		height: 100%;
		padding: 5px;
		font-size: 16px;
		font-family: '微软雅黑';
		border: 1px #cccccc solid;
		appearance: none;
		-moz-appearance: none;
		-webkit-appearance: none;
		background: url("../assets/triangle.jpg") no-repeat scroll right;
		background-color: #ffffff;
		border-radius: 5px;
	}
</style>
