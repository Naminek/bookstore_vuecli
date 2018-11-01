<template>
	<div id="app">
    <div v-if="isLoading">
      <!-- <img alt="loading" src="../assets/image_now_loading.png"> -->
      <p>is loading...</p>
    </div>
    <div v-slse>
      <header />
      <Book :books="bookData"/>
		<!-- <div id="nav">
			<router-link to="/">Home</router-link> |
			<router-link to="/about">About</router-link>
		</div>
		<router-view /> -->
    </div>
	</div>
</template>

<script>
import Book from "@/components/Book.vue";
import Header from "@/components/Header.vue";
export default {
  components: {
    Book,
    Header
  },
  data() {
    return {
	  bookData: [],
	  isLoading: true
    };
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
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

/* #nav {
		padding: 30px;
	}

	#nav a {
		font-weight: bold;
		color: #2c3e50;
	}

	#nav a.router-link-exact-active {
		color: #42b983;
	} */
</style>
