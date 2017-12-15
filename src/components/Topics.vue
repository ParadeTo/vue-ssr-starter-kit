<template>
  <div>
    <div v-for="topic in topics">
      <p>{{topic.title}}</p>
    </div>
  </div>
</template>

<script>
import { mapGetters } from 'vuex'

export default {
  computed: {
    ...mapGetters({
      topics: 'getTopics'
    })
  },

  asyncData ({ store }) {
    console.log('这是个啥！')
    return store.dispatch(`getTopics`)
  }
}
</script>
