<template>
  <div class="col-large push-top">
    <h1>Welcome to the forum</h1>
    <ThreadList />
  </div>
 
</template>

<script>

import sourceData from '@/data'

export default {
  name: 'HelloWorld',
  data () {
    return {
      threads: sourceData.threads,
      posts: sourceData.posts,
      users: sourceData.users
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
