<template>
	<div ref='root' @click="upload" class="wish-page-components">
		<img ref='img' :src='src' />
	</div>
</template>

<script>
	import WishBaseComponent from './BaseComponent.vue'
	export default {
		extends: WishBaseComponent,
		name: 'wish-upload',
		props: ['src'],
		created() {
			this.test = true;
		},
		methods: {
			upload() {
				this.$refs['img'].style.display = 'block';
			},
			valid() {
				return this.$refs['img'].style.display == 'block';
			}
		}
	}
</script>

<style scoped>
	.wish-page-components {
		cursor: pointer;
	}

	img {
		display: none;
		width: 100%;
		height: 100%;
	}
</style>
