<template>
	<div>
  <div v-for="(oneBook, index) in oneBookData" :key="index"> 
    <img alt="book_cover[[index]]" src="oneBook.cover">
    <div class="caption">
    	<h3 class="book_title">{{oneBook.title}}</h3>
    	<p class="book_detail">{{oneBook.description}}</p>
    	<button  type="button" class="more_info" value="index">More Info</button>
    </div>
  </div>
	</div>
</template>

<script>
export default {
  name: "oneBookData",
  props: ["oneBookData"]
};
</script>

<style>
</style>