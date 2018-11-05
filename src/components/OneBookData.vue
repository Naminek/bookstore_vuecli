<template>
	<div>
  <div v-for="(oneBook, index) in oneBookData" :key="index"> 
    <img :alt="`book_image${ index }`" :src="oneBook.cover">
    <div class="caption">
    	<h3 class="book_title">{{oneBook.title}}</h3>
    	<p class="book_detail">{{oneBook.description}}</p>
    	<button type="button" class="more_info" 
      :data-link="`${oneBook.detail}`" :value="`${ index }`" @click="showCover($event)">More Info</button>
    </div>
  </div>
	</div>
</template>

<script>
export default {
  name: "oneBookData",
  props: ["oneBookData"],
  data(){
    return{
      pushedButton: ""
    }
  },
  methods: {
    showCover(ev){
      // console.log(ev.target.value);
      this.pushedButton = ev.target.value;
      console.log(this.pushedButton);
    }
  }
};
</script>

<style>
</style>