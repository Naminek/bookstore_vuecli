<template>
  <div>
    <div v-for="(oneBook, ind) in bookComponents" :key="ind">
      <img src="oneBook.cover">
      <div class="caption">
        <h3 class="book_title">{{oneBook.title}}</h3>
        <p class="book_detail">{{oneBook.description}}</p>
        <button  type="button" class="more_info" value="">More Info</button>
    	</div>
    </div>
  </div>
</template>

<script>
export default {
  name: "bookComponents",
  props: ["bookComponents"]
};
</script>

<style scoped>
p {
  margin: 40px 0 0;
}
</style>