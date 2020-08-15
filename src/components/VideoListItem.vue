<template>
	<li class="list-group-item">
		{{ video.title }}
	</li>
</template>

<script>
export default {
	name: "VideoListItem",
	props: {
		video: Object
	}
}
</script>

<style scoped>

</style>