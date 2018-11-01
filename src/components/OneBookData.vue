<template>
<div>
    <h3>{{oneBookData.title}}</h3>
    <p>{{oneBookData.description}}</p>
    <!--  <div class="caption">
        <img src="{{oneBookData.cover}}">
    <h3 class="book_title">{{oneBookData.title}}</h3>
    <p class="book_detail">{{oneBookData.description}}</p>
    <button  type="button" class="more_info" value="">More Info</button>
    </div> -->
    </div>
</template>

<script>
export default {
    name: 'oneBookData',
    props: ['oneBookData']
}
</script>

<style>
</style>