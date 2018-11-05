<template>
  <div>
		<span class="close">&times;</span>
		<span class="previous_cover ml-3">&#60;</span>
		<img :src="slideShow" alt="`book_cover">
		<span class="next_cover">&#62;</span>
	</div>
</template>

<script>
// import OneBookData from "@/components/OneBookData.vue";
export default {
  name: "slideShow",
	props: ["slideShow"],
	// components: {
	// 	OneBookData
	// },
	// data(){
	// 	return{

	// 	}
	// }
};
</script>

<style>
</style>