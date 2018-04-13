<template>
	<div>
		{{name}} har {{amount}} pengar.
	</div>
</template>

<script>
export default {
	props: ['amount', 'name']
};
</script>

<style scoped>

</style>
