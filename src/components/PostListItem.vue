<template>
  <div class="post">
        <div class="user-info">
          <a href="#" class="username">{{user.name}}</a>
          <a href="#">
            <img class="avatar-large" :src="user.avatar" alt="">
          </a>
          <p class="desktop-only text-small">{{userPostsCount}} posts</p>
        </div>
        <div class="post-content">
          <div>
            <p>
              {{post.text}}
            </p>
          </div>
        </div>
        <div class="post-date text-faded">
          {{post.publishedAt}}
        </div>
  </div>
</template>
<script>
import SourceData from '@/data'
export default {
  props: {
    post: {
      required: true,
      type: Object
    }
  },
  computed: {
    user () {
      return SourceData.users[this.post.userId]
    },
    userPostsCount () {
      const postNumber = this.user.posts ? Object.keys(this.user.posts).length : 0
      return postNumber
    }
  }
}
</script>
<style module>

</style>