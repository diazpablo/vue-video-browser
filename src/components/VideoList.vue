<template>
	<ul>
		<VideoListItem/>
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