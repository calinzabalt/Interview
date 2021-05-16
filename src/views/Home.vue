<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/reddit.svg">
    <ListContainer/>
    
  </div>
</template>

<script>
import ListContainer from '@/components/ListContainer.vue'

export default {
  name: 'Home',
  components: {
    ListContainer
  }
}

</script>
<style scoped>
  .home img{
    max-width: 80px;
  }
</style>
