<template>
  <div class="col-large push-top">
    <div>
      <h2>{{thread.title}}</h2>
      <PostList 
        :posts="posts"
      />
      <form @submit.prevent="addToPost">
        <div class="form-group">
          <textarea 
          name="" 
          id="" 
          cols="30" 
          rows="10" 
          class="form-input"
          v-model="newPostText"
          >
          </textarea>
        </div>
        <div class="form-actions">
          <button class="btn btn-blue">Submit post</button>
        </div>
      </form>
    </div>
  </div>
 
</template>

<script>
import Vue from 'vue'
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
      // posts: sourceData.posts,
      users: sourceData.users,
      newPostText: ''
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
    addToPost () {
      const postId = 'greatPost' + Math.random()
      const post = {
        text: this.newPostText,
        publishedAt: Math.floor(Date.now() / 1000),
        threadId: this.id,
        userId: '38St7Q8Zi2N1SPa5ahzssq9kbyp1',
        '.key': postId
      }
      this.$set(sourceData.posts, postId, post)
      this.$set(this.thread.posts, postId, postId)
      this.users[post.userId].posts = this.users[post.userId].posts ? this.users[post.userId].posts : []
      this.$set(this.users[post.userId].posts, postId, postId)
      this.newPostText = ''
    }
  }
}
</script>
<style lang="css" scoped>

</style>