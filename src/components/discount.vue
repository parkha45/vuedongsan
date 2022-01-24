<template>
	<div class="discount">
		<h2>여긴 광고다~~</h2>
		<h3>지금 클릭하시면 킹갓제너럴캡멋진방이 {{ discountPrice }}% 할인! </h3>
		<p>광고 광고 광고 광고 광고 광고 광고 광고 광고</p>
	</div>
</template>

<script>
export default {
	name:'Discount',
	props: {
		discountPrice : Number,
	}
}
</script>

<style>

</style>
