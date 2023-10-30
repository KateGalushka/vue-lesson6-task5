<template>
	<div class="container">
		<product-card
		v-for="card in cardList" :key="card.id"
		:product-data="card"
		/>
	</div>
	
</template>

<script>
import ProductCard from './ProductCard.vue'

	export default {
		name: "ProductPanel",

		components: { ProductCard },

		props: {
			cardList:{
				type: Array,
				default: ()=>[]
			} 
		}
	}
</script>

<style lang="css" scoped>
.container{
	display: flex;
	flex-wrap: wrap;
	/* align-items: center; */
	justify-content: center;
}

</style>