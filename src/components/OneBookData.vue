<template>
	<div>
  <div v-for="(oneBook, index) in oneBookData" :key="index"> 
    <img :alt="`book_image${ index }`" :src="oneBook.cover">
    <div class="caption">
    	<h3 class="book_title">{{oneBook.title}}</h3>
    	<p class="book_detail">{{oneBook.description}}</p>
    	<button type="button" class="more_info" :data-link="`${oneBook.detail}`" 
      :value="`${ index }`" @click="showCover($event)"  id="cover">More Info</button>
    </div>
  </div>
    <slideShow :slideShow="coverUrl" id="photo_gallery" />
	</div>
</template>

<script>
import SlideShow from "@/components/SlideShow.vue";
export default {
  name: "oneBookData",
  props: ["oneBookData"],
  components: {
    SlideShow
  },
  data(){
    return{
      pushedButton: "",
      coverUrl: ""
    }
  },
  methods: {
    showCover(ev){
      // console.log(ev.target.value);
      this.pushedButton = ev.target.value;
      console.log(this.pushedButton);
      var otherCover = document.getElementById('cover');
      this.coverUrl = otherCover.dataset.link;
      console.log(this.coverUrl);
    }
  }
};
</script>

<style>
</style>