<template>
  <div>
		<div>
			<span class="close">&times;</span>
			<!-- <span class="previous_cover ml-3">&#60;</span> -->
			<img :src="slideShow" alt="`book_cover">
			<!-- <span class="next_cover">&#62;</span> -->
		</div>
	</div>
</template>

<script>

export default {
  name: "slideShow",
	props: ["slideShow"]
};
</script>

<style>
</style>