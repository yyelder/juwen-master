<template>
	<div ref='root' @click="clickHandler" class="wish-page-components">
	</div>
</template>

<script>
	import WishBaseComponent from './BaseComponent.vue'
	export default {
		extends: WishBaseComponent,
		name: 'wish-button',
		props: {
			submit: Boolean,
			event: String,
			once: {
				default: true
			}
		},
		created() {
			this.test = true;
		},
		data() {
			return {
				clicked: false
			}
		},
		methods: {
			clickHandler() {
				if (this.once && this.clicked && !this.submit)
					return;
				this.clicked = true;
				this.$emit('click');
			},
			valid() {
				return this.clicked;
			}
		}
	}
</script>

<style scoped>
	.wish-page-components {
		cursor: pointer;
	}
</style>
