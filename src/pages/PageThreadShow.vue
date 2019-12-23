<template>
  <div class="col-large push-top">
    <div>
      <h2>{{thread.title}}</h2>
      <PostList 
        :posts="posts"
      />
    </div>
  </div>
 
</template>

<script>
import sourceData from '@/data.json'
import PostList from 'comp/PostList'
export default {
  components: {
    PostList
  },
  props: {
    id: {
      required: true,
      type: String
    }
  },
  data () {
    return {
      thread: sourceData.threads[this.id],
      posts: sourceData.posts,
      users: sourceData.users
    }
  },
  computed: {
    posts () {
      const postIds = Object.values(this.thread.posts)
      return Object.values(sourceData.posts)
        .filter(post => postIds.includes(post['.key']))
    }
  }
}
</script>
<style lang="css" scoped>

</style>