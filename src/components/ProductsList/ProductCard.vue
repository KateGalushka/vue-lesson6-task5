<template>
	<div class="container">
		<img :src="productData.imgSrc" width="150">
		<a :href="productData.link" target="_blank">
			<div class="product__desrc">
				<h2> {{ productData.title }}</h2>
				<p class="product__discount">
					Ваша економія: <span style="color:red;">{{ productData.discount }}₴</span> 
				</p>
				<p class="product__old-price"> 
					<span style="text-decoration: line-through;"> {{ productData.oldPrice }}</span> ₴
				</p>
				<div>
					<p class="product__price">
						<span style="font-size: 24px;">{{ productData.price }} ₴</span> 
						<button>Купити</button>
					</p>
				</div>
			</div>
		</a>
	</div>
</template>

<script>
	export default {
		name: "ProductCard",

		props: {
			productData: {
				type: Object,
				default: ()=>({}),
			},
		},
	}
</script>

<style lang="css" scoped>
.container{
	display: flex;
	flex-direction: column;
	margin: 15px;
	align-items: center;
	gap: 20px;
	max-width: 25vw;
	border: .5px solid grey;
	padding: 5px;
}
.product__descr {
	display: flex;
	flex-direction: column;
	padding: 20px;
}
a{
	text-decoration: none;
}
h2{
	color:rgb(107, 107, 167);
	font-size: 20px;
	margin: 10px 0;
}
.product__discount {
	margin: 0;
	font-size: 12px;
	color: rgb(37, 37, 37);
}
.product__old-price{
	color: rgb(37, 37, 37);
	font-size: 14px;
}
.product__price{
	color:red;
	font-weight: 600;
	display: flex;
	justify-content: space-between;
}
button{
	background-color: green;
	color:#fff;
	padding: 10px 20px;
	margin-right: 10px;
	border: none;
	border-radius: 5px;
}

</style>