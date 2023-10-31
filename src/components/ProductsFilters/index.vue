<template>
	<div>
		<stores-filter v-model.check="checkedStores" :stores-list="stores"/>
		<brands-filter v-model.check="checkedBrands" :brand-names-list="brandList"/>
	</div>
</template>

<script>
import { stores } from '@/constants/stores.js';
import { brandList } from '@/constants/brands.js';
import StoresFilter from './StoresFilter.vue';
import BrandsFilter from './BrandsFilter.vue';

export default {
	name: 'FilterManager',
	components: {
		StoresFilter, BrandsFilter
	},
	data() {
		return {
			stores,
			brandList,
			checkedStores: [],
			checkedBrands: []
		}
	},
	watch: {
		checkedStores(newValue) {
			this.$emit('areCheckedStores', newValue);
			// console.log('oldVAlue:', oldValue);
		},
		checkedBrands(newValue) {
			this.$emit('areCheckedBrands', newValue);
			// console.log('oldValue:', oldValue);
		}
	},
}
</script>

<style lang="scss">
.filters
{
	display: flex;
	flex-direction: column;
	border: 1px solid #000;
	margin-bottom: 20px;
	padding: 15px;
}

.noSelected
{
	border: 3px dashed green;
}
</style>