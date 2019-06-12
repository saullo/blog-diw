<template>
  <div>
    <v-card>
      <v-card-title primary-title>
        <div>
          <h3 class="headline mb-0">Criar uma postagem</h3>
        </div>
      </v-card-title>
      <v-card-text>
        <v-form v-on:submit.prevent="validate()">
          <v-text-field label="Titulo" box name="title" v-model="title" v-validate="'required'" :error-messages="errors.collect('title')"/>
          <v-textarea label="Conteudo" box name="content" v-model="content" v-validate="'required'" :error-messages="errors.collect('content')"/>
          <v-btn type="submit" outline color="primary" :disabled="loading" :loading="loading">Postar</v-btn>
        </v-form>
      </v-card-text>
    </v-card>
  </div>
</template>

<script>
import { setTimeout } from 'timers';
export default {
  data () {
    return {
      title: '',
      content: '',
      loading: false,
    }
  },
  methods: {
    validate () {
      this.$validator.validate().then((response) => {
        if (response) this.create()
      })
    },
    create () {
      this.loading = true

      let posts = JSON.parse(localStorage.getItem('dbSaulloBretas'))
      let id = posts.length
      let date = new Date()
      let year = date.getFullYear()
      let month = date.getMonth() + 1
      let day = date.getDate()
      let fullDate = `${day}/${month}/${year}`
      let post = {
        id: id,
        title: this.title,
        content: this.content,
        likesCount: 0,
        commentsCount: 0,
        liked: false,
        comments: [],
        date: fullDate
      }

      posts.unshift(post)
      localStorage.setItem('dbSaulloBretas', JSON.stringify(posts))

      setTimeout(() => {
        this.$router.push('/')
      }, 1000)
    }
  }
}
</script>

<style>

</style>
