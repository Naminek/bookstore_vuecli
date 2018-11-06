<template>
	<div id="app">
    <div v-if="isLoading" id="loading">
      <img alt="loading" src="./assets/image_now_loading.png">
    </div>
    <div v-else id="container" class="d-flex">
			<div id="logo">
     		 <img alt="logo1" src="./assets/red.png">
     		 <img alt="logo2" src="./assets/gray.png">
     		 <img alt="logo3" src="./assets/blue.png">
			</div>
			<div id="page_title" class="d-flex">
    		<h1>Namine's Book Store</h1>
			</div>
			<div id="search_engine">
				<label for="book_search">
					<img class="search_icon" src="./assets/search_icon.png">
			    <input id="book_search" v-model="searchWords" placeholder="Search by keyword" size="30">
				</label>
			</div>
      <OneBookData :oneBookData="findBooks" id="book_list"/>
			<!-- <slideShow :slideShow="coverUrl" id="photo_gallery" class="other_cover" /> -->
    </div>
  </div>
</template>

<script>
import OneBookData from "@/components/OneBookData.vue";
// import SlideShow from "@/components/SlideShow.vue";
export default {
  components: {
    OneBookData,
  },
  data() {
    return {
			bookData: [],
			searchWords: "",
      isLoading: true
    };
	},
	computed: {
		findBooks() {
			if (this.searchWords == "") {
				return this.bookData;
			} else {
				// console.log(this.searchWords);
				return this.bookData.filter
				(book => (book.title.toUpperCase().includes(this.searchWords.toUpperCase()) 
				|| book.description.toUpperCase().includes(this.searchWords.toUpperCase())));
			}
		}
	},
  created() {
    this.loadData();
  },
  methods: {
    loadData() {
      fetch("https://api.myjson.com/bins/zyv02", {
        method: "GET",
        headers: {
          "Content-Type": "application/json"
        }
      })
        .then(response => {
          return response.json();
        })
        .then(json => {
          this.bookData = json.books;
          this.isLoading = false;
        })
        .catch(function(error) {
          console.log(error);
        });
		}
  }
};
</script>


<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  color: #2c3e50;
}

#loading {
	position: absolute;
	top: 100px;
	left: 46%;
}
#loading img {
	width: 100%;
}

#container {
  display: grid; 
	grid-template-rows: 150px 1fr;
  grid-template-columns: 1fr 2fr 1fr;
	padding: 30px;
	align-items: flex-end;
}

#logo {
  grid-row: 1;
  grid-column: 1;
}

#logo img{
	max-width: 50px;
}

#page_title {
	grid-row: 1;
  grid-column: 2;
	display: flex;
	align-items: baseline;
}

h1 {
	font-size: 4vmax;
}

#search_engine {
  grid-row: 1;
  grid-column: 3;
	display: inline;
	/* align-items: baseline; */
}

.search_icon {
	width: 30px;
	/* margin: 0; */
}

#search_engine input{
	margin-bottom: 20px;
}

#book_list {
	grid-row: 2;
	grid-column: 1 / 4;
	display: flex;
	flex-wrap: wrap;
}

#book_list div:not(:last-child) {
	width: 30%;
	margin: 1%;
	position: relative;
	display: block;
	cursor: pointer;
	overflow: hidden;
	border: 3px solid #fff;
}


#book_list div .first_img {
	width: 100%;
	transition: all .8s ease-out;
}

#book_list div:hover .first_img {
	opacity: .4;
	transform: scale(1.3);
}


#book_list div:hover .caption {
	filter: alpha(opacity=100);
	opacity: 1;
	-webkit-transform: rotate(0);
	-moz-transform: rotate(0);
	-o-transform: rotate(0);
	-ms-transform: rotate(0);
	transform: rotate(0);
	top: 0;
}

#book_list div .caption {
	margin: 2%;
	filter: alpha(opacity=0);
	opacity: 0;
	position: absolute;
	height: 96%;
	width: 95%;
	top: -100%;
	background: rgba(0, 0, 0, .7);
	color: #fff;
	-webkit-transition: all .5s ease;
	-moz-transition: all .5s ease;
	-o-transition: all .5s ease;
	-ms-transition: all .5s ease;
	transition: all .5s ease;
	-webkit-transition-delay: .5s;
	-moz-transition-delay: .5s;
	-o-transition-delay: .5s;
	-ms-transition-delay: .5s;
	transition-delay: .5s;
	-webkit-transform: rotate(360deg);
	-moz-transform: rotate(360deg);
	-o-transform: rotate(360deg);
	-ms-transform: rotate(360deg);
	transform: rotate(360deg);

}

#book_list div .caption .book_title {
	font-weight: 400;
	color: #f3c704;
	padding: 20px 20px 0;
	margin-bottom: 0;
	position: relative;
	left: 100%;
	margin-top: 5px;
	font-size: 25px;
	-webkit-transition: all .5s;
	-moz-transition: all .5s;
	-o-transition: all .5s;
	-ms-transition: all .5s;
	transition: all .5s;
	-webkit-transition-delay: 1s;
	-moz-transition-delay: 1s;
	-o-transition-delay: 1s;
	-ms-transition-delay: 1s;
	transition-delay: 1s;
}

#book_list div .caption .book_detail,
#book_list div .caption button {
	padding: 10px 20px;
	margin-bottom: 0;
	position: relative;
	left: 100%;
	font-size: 16px;
	-webkit-transition: all .5s;
	-moz-transition: all .5s;
	-o-transition: all .5s;
	-ms-transition: all .5s;
	transition: all .5s;
	-webkit-transition-delay: 1.3s;
	-moz-transition-delay: 1.3s;
	-o-transition-delay: 1.3s;
	-ms-transition-delay: 1.3s;
	transition-delay: 1.3s;
}

#book_list div:hover .caption h3,
#book_list div:hover .caption p,
#book_list div:hover .caption button {
	left: 0;
}

#book_list div .caption button {
	color: #fff;
	border: 2px solid #fff;
	padding: 4px 10px;
	text-decoration: none;
	background-color: rgba(0, 0, 0, .5);
	margin: 10px 20px;
}

#book_list div .caption button:hover {
	color: #4f5856;
	background: #fff;
	transition: 0.2s;
}

</style>
