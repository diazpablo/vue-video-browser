<template>
	<div>
		<form @submit.prevent="onSubmit" class="d-flex py-4 px-5">
			<input class="form-control" type="text" name="search" autofocus />
			<input class="btn btn-primary ml-4" type="submit" value="Search" />
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

<style scoped>

</style>