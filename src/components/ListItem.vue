<template>
  <div class="list_item">
    <a :href="`https://www.reddit.com${blog.permalink}`" target="_blank"><p>{{blog.title}}</p></a>
    <img v-if="blog.thumbnail" v-bind:src="blog.thumbnail">
    <h4>{{blog.subreddit_name_prefixed}}</h4>
  </div>
</template>

<script>
export default {
  name: 'ListItem',
  props: ["blog"],
}
</script>

<style scoped>
  
</style>

