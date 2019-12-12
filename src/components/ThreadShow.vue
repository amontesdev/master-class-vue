<template>
  <div class="col-large push-top">
    <div v-for="thread in threads" :key="thread.id">
      <h2>{{thread.title}}</h2>
      <div class="post-list">
        <div class="post" v-for="postId in thread.posts" :key="postId">
          <div class="user-info">
            <a href="#" class="username">{{users[posts[postId].userId].name}}</a>
            <a href="#">
              <img class="avatar-large" :src="users[posts[postId].userId].avatar" alt="">
            </a>
            <p class="desktop-only text-small"></p>
          </div>
          <div class="post-content">
            <div>
              <p>
                {{posts[postId].text}}
              </p>
            </div>
          </div>
          <div class="post-date text-faded">

          </div>
        </div>
      </div>
    </div>
  </div>
 
</template>

<script>
export default {
    props:{
        id:{
            required:true,
            type:String
        }
    }
}
</script>
<style lang="css" scoped>

</style>