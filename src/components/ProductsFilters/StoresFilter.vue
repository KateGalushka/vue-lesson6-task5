<template>
	<div 
	class="filters" 
	:class="{'noSelected': !checkIfItemSelected }"
	>
	<h2>Продавець:</h2>
	<label v-for="store in storesList" :key="store.id">
		<input v-model="currentStoresChecked" type="checkbox"  :value="store">
				{{ store.title }}
	</label>
	
	</div>
</template>

<script>
	export default {
    name: 'StoresFilter',

	 props: {
		storesList: {
			type: Array,
			default: ()=>[]
		},
		modelValue: {
			type: Array,
			default: ()=>([])
		},
		modelModifiers: {
			default: () => ({})
		}
	 },

    data() {
		return {
			checkedItems: [],
		}
	 },
	 computed: {
		currentStoresChecked: {
			get() {
				return this.modelValue;
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