<template>
	<div class="filters" 
	:class="{'noSelected': !checkIfItemSelected() }"
	>
	<h2>Продавець:</h2>
	<filter-item
		v-for="item in storesNames" :key="item.id"
			:itemCard="item"
			v-model.checkSelection="checkedItems"
			@checkSelection="checkIfItemSelected"
	/>
	</div>
</template>

<script>
import {storesNames} from '@/constants/stores.js'
import FilterItem from './FilterItem.vue';

	export default {
    name: 'StoresFilter',

	 components: { FilterItem },

    data() {
		return {
			storesNames,
			checkedItems: [],
		}
	 },
	 methods: {
		checkIfItemSelected() {
			return (this.checkedItems.length > 0)
		}
	 }

}
</script>

<style lang="scss" scoped>

</style>