<template>
	<div class="preview">
		<div v-for="(url, index) in urls" :key="index" :style="{ 'background-image': `url(${url})` }" class="image">
			<span class="badge bg-danger" @click="removeImage(index)">
				<i class="bi bi-x-lg"></i>
			</span>
		</div>
	</div>
</template>

<script lang="ts">
import { defineComponent } from 'vue'

export default defineComponent({
	props: {
		urls: {
			type: Object,
			required: true
		}
	},

	emits: ['remove'],

	methods: {
		removeImage(index: number) {
			this.$emit('remove', index)
		}
	}
})
</script>

<style lang="scss" scoped>
.preview {
	margin: 20px 0;
	display: flex;
	gap: 10px;
	justify-content: left;
	align-items: center;
	.image {
		$width: 190px;
		width: $width;
		height: $width * 3 / 4;
		background-size: cover;
		background-position: center;
		border-radius: 10px;
		position: relative;
		@include media-breakpoint-down(md) {
			width: 90px;
			height: 90px * 3 / 4;
		}
		> span {
			position: absolute;
			right: 0;
			width: 28px;
			height: 28px;
			padding: 0;
			display: flex;
			justify-content: center;
			align-items: center;
			cursor: pointer;
		}
	}
}
</style>
