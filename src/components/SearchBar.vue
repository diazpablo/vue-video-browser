<template>
	<div>
		<form @submit.prevent="onSubmit">
			<input type="text" name="search" />
			<input type="submit" value="Search" />
		</form>
	</div>
</template>

<script>
export default {
	name: 'SearchBar',
	methods: {
		onSubmit(e) {
			this.$emit('termChange', e.target.elements.search.value);
		}
	}
}
</script>

<style>
</style>