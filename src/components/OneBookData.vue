<template>
	<div>
    <div v-for="(oneBook, index) in oneBookData" :key="index"> 
      <img :alt="`book_image${ index }`" :src="oneBook.cover" class="first_img">
      <div class="caption">
    	  <h3 class="book_title">{{oneBook.title}}</h3>
    	  <p class="book_detail">{{oneBook.description}}</p>
    	  <button type="button" class="more_info" :data-link="`${oneBook.detail}`" 
        :value="`${ index }`" @click="showCover($event, oneBook)"  id="cover">More Info</button>
      </div>
    </div>
    <slideShow :slideShow="coverUrl" id="photo_gallery" class="other_cover" />
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
    showCover(ev, book){
      // console.log(ev.target.value);
      this.pushedButton = ev.target.value;
      console.log(this.pushedButton);
      // var otherCover = document.getElementById('cover');
      // this.coverUrl = otherCover.dataset.link;
      console.log(book.detail);
      this.coverUrl = book.detail;
      
      function printImage() {
        var showCover = document.getElementById('photo_gallery');
        showCover.style.display = "block";

		    var spanToClose = document.getElementsByClassName("close")[0];
		    spanToClose.onclick = function () {
			    showCover.style.display = "none";
		    }
	  }
	printImage();
    }
  }
};
</script>

<style>
.other_cover {
	display: none;
	position: fixed;
	z-index: 1;
	padding-top: 40px;
	left: 0;
	top: 0;
	width: 100%;
	height: 100%;
	background-color: rgb(0, 0, 0);
	background-color: rgba(0, 0, 0, 0.4);
}

.other_cover div {
	background-color: #fefefe;
	margin: auto;
	padding: 20px;
	border: 1px solid #888;
	width: 55%;
}

.other_cover div img {
	width: 85%;
}

.close {
	color: #ffffff;
	float: right;
  position: absolute;
  top: 5%;
  right: 10%;
	font-size: 40px;
	font-weight: bold;
}

.close:hover,
.close:focus,
.previous_cover:hover,
.previous_cover:focus,
.next_cover:hover,
.next_cover:focus {
	color: #000;
	text-decoration: none;
	cursor: pointer;
}

.previous_cover,
.next_cover {
	color: #aaaaaa;
	font-size: 40px;
	font-weight: bold;
}

</style>