<template>
  <div class="col-full">
    <h1>Welcome to the forum</h1>
    <ForumList :forums="forums"/>
  </div>
 
</template>

<script>

import sourceData from '@/data'
import ForumList from 'comp/ForumList'

export default {
  name: 'HelloWorld',
  components: {
    ForumList
  },
  data () {
    return {
      forums: Object.values(sourceData.forums),
      posts: sourceData.posts,
      users: sourceData.users
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
