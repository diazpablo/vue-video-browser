<template>
	<li class="list-group-item media" @click="onVideoSelect">
		<img
			class="mr-3"
			:src="thumbnailUrl"
			:alt="video.snippet.title" :title="video.snippet.title"
		/>
		<div class="media-body">{{ video.snippet.title }}</div>
	</li>
</template>

<script>
	export default {
		name: "VideoListItem",
		props: {
			video: Object
		},
		computed: {
			thumbnailUrl() {
				return this.video.snippet.thumbnails.default.url
			}
		},
		methods: {
			onVideoSelect() {
				this.$emit('videoSelect', this.video)
			}
		}
	}
</script>

<style scoped>
	li {
		display: flex;
		align-items: center;
		cursor: pointer;
	}
	
	li img {
		transition: transform .4s;
	}
	
	li:hover {
		background-color: #eee;
		z-index: 1;
	}
	
	li:hover img {
		transform: scale(1.05);
	}
</style>