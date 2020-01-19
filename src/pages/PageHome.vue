<template>
  <div class="col-full">
    <h1>Welcome to the forum</h1>
    <CategoryList :categories="categories"/>
  </div>
 
</template>

<script>

import sourceData from '@/data'
import CategoryList from 'comp/CategoryList'

export default {
  name: 'HelloWorld',
  components: {
    CategoryList
  },
  data () {
    return {
      categories: Object.values(sourceData.categories)
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
