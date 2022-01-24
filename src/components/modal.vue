<template>
	<div class="black-bg" v-if="modal_bool == true">
		<div class="white-bg">
			<h4> {{ oneroom_data[get_product_num].title }} </h4>
			<p>{{ oneroom_data[get_product_num].content }}</p>
			<p> {{ month }}개월 선택함 :  {{ oneroom_data[get_product_num].price * month }}</p>

			<input v-model="month">

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
			if( isNaN(a) == true || a > 12 ) {
				this.month = 12
			}
		}
	},
	beforeUpdate() {
		if( this.month == 2 ) {
			alert("최소 3개월부터 가능합니다.")
			this.month = 3
		}
	},
	updated() {

	},
	props: {
		oneroom_data : Array,
		modal_bool : Boolean,
		get_product_num : Number
	}
}
</script>

<style>

</style>
