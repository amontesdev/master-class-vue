<template>
  <div class="col-large push-top">
    <div>
      <h2>{{thread.title}}</h2>
      <p>
        By <a href="" class="link-unstyled">Andres</a>, <BaseDate :timestamp="thread.publishedAt" />
      </p>
      <PostList 
        :posts="posts"
      />
      <PostEditor 
      @savePost="addPost"
      :threadId="id"
      />
    </div>
  </div>
 
</template>

<script>
import Vue from 'vue'
import sourceData from '@/data.json'
import PostList from 'comp/PostList'
import PostEditor from 'comp/PostEditor'
export default {
  components: {
    PostList,
    PostEditor
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
      // posts: sourceData.posts,
      users: sourceData.users
    }
  },
  computed: {
    posts () {
      const postIds = Object.values(this.thread.posts)
      return Object.values(sourceData.posts)
        .filter(post => postIds.includes(post['.key']))
    }
  },
  methods: {
    addPost ({post}) {
      const postId = post['.key']
      this.$set(sourceData.posts, postId, post)
      this.$set(this.thread.posts, postId, postId)
      this.users[post.userId].posts = this.users[post.userId].posts ? this.users[post.userId].posts : []
      this.$set(this.users[post.userId].posts, postId, postId)
    }
  }
}
</script>
<style lang="css" scoped>

</style>