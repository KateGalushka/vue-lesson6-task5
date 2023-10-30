<template>
	<div>
		<label>
			<input type="checkbox" v-model="isChecked" :value="itemCard.id">
			{{ itemCard.title }}
		</label>

	</div>
</template>

<script>
	export default {
		name: 'FilterItem',
		props: {
			itemCard: {
				type: Object,
				default: ()=>({})
			},
			modelValue: {
				type: Array,
				default: ()=>[]
			},
			modelModifiers: {
				default: ()=>({})
			}
		},
		data() {
			return {
				isItemSelected: false
			}
		},
		computed: {
			isChecked: {
				get(){
					return this.modelValue.includes(this.itemCard.id);
				},
				set(val){
					const newVal = [...this.modelValue];
					if (val) {
						newVal.push(this.itemCard.id);
					} else {
						const index = newVal.indexOf(this.itemCard.id);
						if (index !==-1) {
							newVal.splice(index,1);
						}
					};
					this.$emit('update:modelValue', newVal);

					if (this.modelModifiers.checkSelection) {
						this.$emit('checkSelection', val)
					}
				}
			}
		},
	}
</script>

<style lang="scss" scoped>

</style>