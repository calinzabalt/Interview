<template>
  <div class="container">
    <h1>Reddit List of posts</h1>
    <paginate class="posts_container"
      name="blogs"
      :list="posts"
      :per="25"
      tag="div"
    >
    <ListItem
      v-for="blog in paginated('blogs')" 
      v-bind:key="blog.id"
      :blog="blog.data">
    </ListItem>
    </paginate>
    <paginate-links
          for="blogs"
          :async="true"
          :show-step-links="true"
          :step-links="{
            next: 'Next',
            prev: 'Previous'
          }"
          :classes="{
            'ul': 'pagination',
            'ul > li': 'page-item',
            'ul > li > a': 'page-link',
          }"  
        >
    </paginate-links>
  </div>
</template>

<script>
import Vue from 'vue'
import VueAxios from 'vue-axios'
import axios from 'axios'
import ListItem from '../components/ListItem'

Vue.use(VueAxios, axios)

export default {
  name: 'ListContainer',
  components: {
    ListItem
  },
  data () {
    return {
      posts: [],
      paginate: ['blogs']
    }
  },
  mounted() {
    Vue.axios.get('https://www.reddit.com/r/aww/new.json?limit=100')
    .then((res) => {
      this.posts = res.data.data.children
      console.log(res.data.data.children)
    })
  }
}
</script>

<style>
  .container{
    max-width: 1180px;
    width: 100%;
    margin-left: auto;
    margin-right: auto;
  }
  .paginate-links{
    display: block;
    margin: 40px 0px;
  }
  .paginate-links li{
    list-style: none;
    display: inline-block;
    margin: 0 10px;
    cursor: pointer;
  }
  .posts_container .list_item{
    border-radius: 4px;
    overflow: hidden;
    position: relative;
    max-width: 640px;
    width: 100%;
    margin: 0 auto;
    background: #ffffff;
    margin-bottom: 20px;
    padding: 20px;
  }
</style>
