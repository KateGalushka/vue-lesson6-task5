<template>
	<div class="filters" 
		:class="{ 'noSelected': !checkIfItemSelected() }"
		>
	<h2>Бренд:</h2>
	<input type="text" placeholder="Пошук"
	 v-model="brandSearchInput"
	>
	<div>

	</div>
	
	  <filter-item
		v-for="brand in filteredBrandList" :key="brand.id"
		:itemCard="brand"
		v-model.checkSelection="checkedItems"
		@checkSelection="checkIfItemSelected"
	/>

	</div>
</template>

<script>
import {brandList} from '@/constants/brands.js';
import FilterItem from './FilterItem.vue';

	export default {
		name: 'BrandsFilter',

		components: { FilterItem },

		data() {
			return {
				brandList,
				checkedItems: [],
				brandSearchInput: null
			}
		},
		computed: {
			filteredBrandList() {
				if (this.brandSearchInput) {
					return this.brandList.filter(brand=> brand.title.toLowerCase().includes(this.brandSearchInput.toLowerCase()))
				}; 
				return this.brandList
				
				
			}
		},
		
		methods: {
			checkIfItemSelected() {
				return (this.checkedItems.length>0)
			}
			
		},
	}
</script>

<style lang="scss" scoped>

</style>