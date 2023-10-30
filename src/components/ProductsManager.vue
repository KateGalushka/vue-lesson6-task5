<template>
	<div class="container-main">
		<filter-manager/>
		<product-panel :cardList="notebooksList"/>

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
			notebooksList
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