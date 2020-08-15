<template>
	<ul class="list-group">
		<VideoListItem
			v-for="video in videos"
			:key="video.etag"
			:video="video.snippet"
		/>
	</ul>
</template>

<script>
import VideoListItem from "@/components/VideoListItem";

export default {
	name: "VideoList",
	components: { VideoListItem },
	props: {
		videos: Array,
	}
}
</script>

<style scoped>
</style>