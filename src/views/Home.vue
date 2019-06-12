<template>
  <div>
    <post v-for="post in posts" :key="post.id" :post="post"/>
  </div>
</template>

<script>
import Post from '@/components/Post'

export default {
  data () {
    return {
      posts: []
    }
  },
  components: {
    Post
  },
  mounted () {
    this.getPosts()
  },
  methods: {
    getPosts () {
      this.posts = JSON.parse(localStorage.getItem('dbSaulloBretas'))
    }
  }
}
</script>

<style>

</style>
