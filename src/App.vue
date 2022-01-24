<template>
	<div id="app">
		<div class="menu">
			<ul>
				<li v-for="iss in menu" :key="iss"><a href=""> {{ iss }} </a></li>
			</ul>
		</div>

		<button @click="priceSort">가격순정렬</button>
		<button @click="backSort">가격순정렬</button>

		<Discount :discountPrice="discountPrice" />

		<!-- <transition name="fade">
			<Modal @closeModal="modal_bool = false" :oneroom_data="oneroom_data" :modal_bool="modal_bool" :get_product_num="get_product_num" />
		</transition> -->

		<div class="fade_in" :class="{ fade_out : modal_bool }">
			<Modal @closeModal="modal_bool = false" :oneroom_data="oneroom_data" :modal_bool="modal_bool" :get_product_num="get_product_num" />
		</div>


		<Card @openModal="modal_bool = true; get_product_num = $event" v-for="(oneroom, i) in oneroom_data" :key="i" :oneroom="oneroom_data[i]" />

	</div>
</template>

<script>

import data from './assets/data/oneroom.js';

import Discount from './components/discount.vue';
import Modal from './components/modal.vue';
import Card from './components/card.vue';

export default {
  name: 'App',
  data() {
		return {
			showDiscount: true,
			discountPrice: 30,
			oneroom_original: [...data],
			oneroom_data: data,
			menu: [ 'home', 'Shop', 'About' ],
			product: ['역삼동원룸', '천호동원룸', '마포구원룸'],
			price: [60, 150, 1000],
			스타일: 'color:blue',
			신고수 : [0, 0, 0],

			modal_bool : false,
			get_product_num : 0
		}
	},
	methods : {
		increase( i ) {
			this.신고수[i]++
		},
		priceSort() {
			this.oneroom_data.sort(function(a, b) {
				return b.price - a.price
			})

			// let data = this.oneroom_data.map( (item)=>{
			// 	return item.price
			// })

		},
		backSort() {
			this.oneroom_data = [...this.oneroom_original]
		},
	},
	mounted() {
		setInterval(()=>{
			if( this.discountPrice > 0 ) {
					this.discountPrice--
			} else {
				clearInterval()
			}
		}, 1000)
	},
	components: {
		Discount : Discount,
		Modal:Modal,
		Card:Card
	}
}
</script>

<style>
	#app {
	-webkit-font-smoothing: antialiased;
	-moz-osx-font-smoothing: grayscale;
	text-align: center;
	color: #2c3e50;
	margin-top: 60px;
	}
	body {
		margin: 0;
		padding: 0;
	}

	li {
		list-style: none;
	}

	div {
		box-sizing: border-box;
	}

	img {
		width: 100%;
	}

	.menu ul {
		display: flex;
		justify-content: center;
		column-gap: 30px;
		padding: 30px 0;
		margin: 0;
	}
	.black-bg {
		width: 100%;
		height: 100%;
		background-color: rgba(0, 0, 0, .5);
		position: fixed;
		padding: 20px;
		top: 0;
		left: 0;
	}
	.white-bg {
		width: 50%;
		background-color: white;
		border-radius: 8px;
		padding: 20px;
		margin: auto;
	}
	.discount {
		width: 100%;
		background-color: #eee;
		border-radius: 5px;
		text-align: center;
		padding: 100px 0;
		margin: auto;
	}

	.fade-enter-from {
		opacity: 0;
	}

	.fade-enter-active {
		transition: all 1s;
	}

	.fade-enter-to {
		opacity: 1;
	}

	.fade-leave-from {
		opacity: 1;
	}

	.fade-leave-active {
		transition: all 1s;
	}

	.fade-leave-to {
		opacity: 0;
	}
</style>

<style lang="scss">
	@import '@/assets/scss/style.scss';
	@import '@/assets/scss/modal.scss';
</style>
