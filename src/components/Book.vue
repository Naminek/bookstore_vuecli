<template>
  <div>
    <OneBookData v-for="(onebook, ind) in books" :key="ind" />
  </div>
</template>

<script>
import OneBookData from "@/components/OneBookData.vue";
export default {
  name: 'book',
  props: ["books"],
  components: {
    OneBookData
  }
}
</script>

<style scoped>
p {
  margin: 40px 0 0;
}
</style>