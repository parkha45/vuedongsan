<template>
	<div class="card-wrap">
		<img :src="oneroom.image" alt="">
		<h3 @click="$emit('openModal', oneroom.id)"> {{ oneroom.title }} </h3>
		<div>{{ oneroom.price }} 원 </div>
	</div>
</template>

<script>
export default {
	name: 'card',
	props: {
		oneroom : Object,
	}
}
</script>

<style>

</style>
