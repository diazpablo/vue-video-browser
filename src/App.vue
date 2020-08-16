<template>
	<div class="container">
		<SearchBar @termChange="onTermChange"></SearchBar>
		<div class="row">
			<div class="col-12 col-lg-7 my-2">
				<VideoDetail :video="selectedVideo" />
			</div>
			<div class="col-12 col-lg-5 my-2 ml-auto">
				<VideoList @videoSelect="onVideoSelect" :videos="videos" />
			</div>
		</div>
	</div>
</template>

<script>
	import axios from 'axios';
	import SearchBar from "@/components/SearchBar";
	import VideoList from "@/components/VideoList";
	import VideoDetail from "@/components/VideoDetail";
	
	const API_KEY = 'AIzaSyAaoCD_Kd7fJUnAd8WAqzFZoJfIbdmQrCM';
	export default {
		name: 'App',
		components: {
			VideoDetail,
			VideoList,
			SearchBar
		},
		data() {
			return {
				videos: [],
				selectedVideo: null
			}
		},
		methods: {
			onVideoSelect(video) {
				console.log(video);
				this.selectedVideo = video;
			},
			onTermChange(term) {
				axios.get('https://www.googleapis.com/youtube/v3/search', {
					params: {
						key: API_KEY,
						type: 'video',
						part: 'snippet',
						q: term,
						relevanceLanguage: 'es'
					}
				})
					.then(({ data }) => {
						this.videos = data.items
					})
			}
		}
	}
</script>