<template>
	<div class="container-main">
		<filter-manager 
			@areCheckedStores="getFilterByStore"
			@areCheckedBrands="getFilterByBrand"/>
		<product-panel :card-list="filteredList"/>

	</div>
</template>

<script>
import { notebooksList } from '@/constants/notebooks';
import FilterManager from './ProductsFilters/index.vue'
import ProductPanel from './ProductsList/index.vue';

export default {
	name: 'ProductsManager',

	components: {
		ProductPanel, FilterManager
	},
	data() {
		return {
			notebooksList,
			checkedStores: [],
			checkedBrands: []

		}
	},
	computed: {
		filteredList() {
			if (this.checkedStores.length == 0 && this.checkedBrands.length == 0) {
				return this.notebooksList
			} else {
				return this.onFilterListData()
			}
		}
	},

	methods: {
		getFilterByStore(checkedStores) {
			this.checkedStores = checkedStores;
			console.log('STORES: ', checkedStores);
		},
		getFilterByBrand(checkedBrands){
			this.checkedBrands = checkedBrands;
			console.log('bRANDS: ', checkedBrands);
		},
		onFilterListData(){
			return this.notebooksList.filter((notebook) => {
				// Check if the seller is in the checkedStores array
				const sellerMatch = !this.checkedStores.length || this.checkedStores.some((store) => store.title === notebook.seller);
				// Check if the brand is in the checkedBrands array
				const brandMatch = !this.checkedBrands.length || this.checkedBrands.some((brand) => brand.title.toLowerCase() === notebook.brand.toLowerCase());

				return brandMatch && sellerMatch;
			});
		}
	},

}
</script>

<style lang="scss" scoped>
.container-main{
	display: grid;
	grid-template-columns: auto auto;
	gap:20px;
}
</style>