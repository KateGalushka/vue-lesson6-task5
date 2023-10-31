<template>
	<div class="filters" 
		:class="{ 'noSelected': !checkIfItemSelected }"
		>
		<h2>Бренд:</h2>
		<input v-model="brandSearchInput" type="text" placeholder="Пошук" >
		<label v-for="brand in filteredBrandList" :key="brand.id">
			<input v-model="currentBrandChecked" type="checkbox"  :value="brand">
				{{ brand.title }}
		</label>
	</div>
</template>

<script>
	export default {
		name: 'BrandsFilter',
		props: {
			brandNamesList: {
				type: Array,
				default: ()=>[]
			},
			modelValue: {
				type: Array,
				default: ()=>[]
			},
			modelModifiers: {
				default: () => ({})
			}
		},

		data() {
			return {
				checkedItems: [],
				brandSearchInput: null
			}
		},
		computed: {
			filteredBrandList() {
				if (this.brandSearchInput) {
					return this.brandNamesList.filter(brand=> brand.title.toLowerCase().includes(this.brandSearchInput.toLowerCase()))
				}; 
				return this.brandNamesList
			},
			currentBrandChecked:{
				get(){
					return this.modelValue
				},
				set(val){
					if (val && this.modelModifiers.check) {
					this.checkedItems = [...val]
					}
					this.$emit('update:modelValue', val)
				}
			},
			checkIfItemSelected() {
				return (this.checkedItems.length > 0)
			}
		},

	}
</script>

<style lang="scss" scoped>

</style>