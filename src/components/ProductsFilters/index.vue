<template>
	<div>
		<stores-filter/>
		<brands-filter/>
	</div>
</template>

<script>
import StoresFilter from './StoresFilter.vue';
import BrandsFilter from './BrandsFilter.vue';

	export default {
		name: 'FilterManager',
		components: {
			StoresFilter, BrandsFilter
		},
	}
</script>

<style lang="scss">
.filters{
	border: 1px solid #000;
	margin-bottom: 20px;
	padding: 15px;
}
.noSelected{
	border:3px dashed green;
}

</style>