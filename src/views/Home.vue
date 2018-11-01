<template>
  <div class="book">
    <!-- <img alt="logo1" src="../assets/red.png">
    <img alt="logo2" src="../assets/gray.png">
    <img alt="logo3" src="../assets/blue.png"> -->
    <Book :books="bookData"/>
  </div>
  <!-- <div class="book">
    <Book msg="Welcome to Your Vue.js App"/>
  </div> -->
</template>

<script>
// @ is an alias to /src
import Book from "@/components/Book.vue";

export default {
  name: "home",
  props: ["bookData"],
  components: {
    Book
  }
};
</script>
