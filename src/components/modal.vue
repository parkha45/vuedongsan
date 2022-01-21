<template>
	<div class="black-bg" v-if="modal_bool == true">
		<div class="white-bg">
			<h4> {{ oneroom_data[get_product_num].title }} </h4>
			<p>{{ oneroom_data[get_product_num].content }}</p>
			<p> {{ month }}개월 선택함 :  {{ oneroom_data[get_product_num].price * month }}</p>

			<!-- <input type="text" @input="month = $event.target.value"> -->
			<input v-model.number="month">

			<button @click="$emit('closeModal', get_product_num)">닫기</button>
		</div>
	</div>
</template>

<script>
export default {
	name: 'Modal',
	data() {
		return {
			month : 1,
		}
	},
	watch: {
		month(a) {
			if( a >= 13 ) {
				month = 12
			}
		}
	},
	props: {
		oneroom_data : Object,
		modal_bool : Boolean,
		get_product_num : Number
	}
}
</script>

<style>

</style>
