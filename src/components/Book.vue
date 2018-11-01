<template>
  <div>
    <p v-for="(onebook, ind) in books" :key="ind">{{ onebook }}</p>
  </div>
</template>

<script>
export default {
  name: 'book',
  props: ["books"],
}
</script>

<style scoped>
p {
  margin: 40px 0 0;
}
</style>