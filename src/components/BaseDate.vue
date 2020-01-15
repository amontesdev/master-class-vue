<template>
  <span
    :title="timestamp | formatDate"
    >
      {{timestamp | formatRelativeDate}}
  </span>
</template>
<script>
import moment from 'moment'

export default {
  props: {
    timestamp: {
      required: true,
      type: Number
    }
  },
  filters: {
    formatDate (date) {
      return moment.unix(date).format('MMM Do YYYY, h:mm:ss a')
    },
    formatRelativeDate (date) {
      return moment.unix(date).fromNow()
    }
  }
}
</script>
<style module>

</style>