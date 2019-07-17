<template>
	<div ref='root' class="wish-page-components"></div>
</template>

<script>
	export default {
		name: 'wish-base-component',
		props: ['left', 'top', 'width', 'height', 'value'],
		data() {
			return {
				test: false
			}
		},
		mounted() {
			this.$refs['root'].style.left = this.left;
			this.$refs['root'].style.top = this.top;
			this.$refs['root'].style.width = this.width;
			this.$refs['root'].style.height = this.height;
		}
	}
</script>

<style>
	.wish-page-components {
		position: absolute;
		background: rgba(0, 0, 0, .3);
	}
</style>
