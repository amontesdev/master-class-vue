<template>
  <form @submit.prevent="addToPost">
    <div class="form-group">
      <textarea 
      name="" 
      id="" 
      cols="30" 
      rows="10" 
      class="form-input"
      v-model="text"
      >
      </textarea>
    </div>
    <div class="form-actions">
      <button class="btn btn-blue">Submit post</button>
    </div>
  </form>
</template>
<script>
export default {
  props: {
    threadId: {
      required: true
    }
  },
  data () {
    return {
      text: ''
    }
  },
  methods: {
    addToPost () {
      const postId = 'greatPost' + Math.random()
      const post = {
        text: this.text,
        publishedAt: Math.floor(Date.now() / 1000),
        threadId: this.threadId,
        userId: '38St7Q8Zi2N1SPa5ahzssq9kbyp1',
        '.key': postId
      }
      this.text = ''
      this.$emit('savePost', {post})
    }
  }
}
</script>