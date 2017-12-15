<template>
  <div>
    <div v-for="topic in list">
      <p>{{topic.title}}</p>
    </div>
  </div>
</template>

<script>
import { mapGetters } from 'vuex'
import request from 'axios'
export default {
  computed: {
    ...mapGetters({
      topics: 'getTopics'
    })
  },

  data () {
    return {
      list: []
    }
  },

  created () {
    const vm = this
    request.defaults.baseURL = 'http://jsonplaceholder.typicode.com/'
    return request.get('posts').then((response) => {
      if (response.statusText === 'OK') {
        vm.list = response.data
      }
    }).catch((error) => {
      console.log(error)
    })
  }
}
</script>
