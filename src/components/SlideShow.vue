<template>
  <div>
		<span class="close">&times;</span>
		<span class="previous_cover ml-3">&#60;</span>
		<img src="' + data[pushedButton].detail + '" alt="book' + pushedButton + '">
		<span class="next_cover">&#62;</span>
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