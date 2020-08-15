<template>
	<div id="app">
		<SearchBar @termChange="onTermChange"></SearchBar>
		<VideoList :videos="videos" />
	</div>
</template>
<script>
import axios from 'axios';
import SearchBar from "@/components/SearchBar";
import VideoList from "@/components/VideoList";

const API_KEY = 'AIzaSyAaoCD_Kd7fJUnAd8WAqzFZoJfIbdmQrCM';
export default {
	name: 'App',
	components: {
		VideoList,
		SearchBar
	},
	data() {
		return {
			videos: []
		}
	},
	methods: {
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