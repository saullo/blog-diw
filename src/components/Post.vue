<template>
  <div>
    <v-card class="mb-2">
      <v-img src="https://picsum.photos/500" aspect-ratio="2"></v-img>
      <v-card-title primary-title>
        <div>
          <h3 class="headline mb-0">{{ post.title }}</h3>
          <div>
            {{ post.date }}
            <v-icon size="20" class="ml-2">thumb_up</v-icon>
            <span class="subheading mx-2">{{ post.likesCount }}</span>
            <v-icon size="20">comment</v-icon>
            <span class="subheading mx-2">{{ post.commentsCount }}</span>
          </div>
        </div>
      </v-card-title>
      <v-card-text>
        <p>{{ post.content }}</p> 
        <template v-if="!post.liked">
          <v-btn outline @click="like()">Curtir</v-btn>
        </template>
        <template v-else>
          <v-btn color="primary"  @click="unlike()">Descurtir</v-btn>
        </template>
        <v-btn outline @click="dialog = !dialog">Comentar</v-btn>
      </v-card-text>
      <v-expansion-panel v-if="post.comments.length > 0">
        <v-expansion-panel-content>
          <template v-slot:header>
            <div>Comentarios</div>
          </template>
          <v-card>
            <v-list v-for="comment in post.comments" :key="comment.id">
              <v-list-tile>
                <v-list-tile-avatar>
                  <img src="https://picsum.photos/50"/>
                </v-list-tile-avatar>
                <v-list-tile-content>
                  <v-list-tile-title>{{ comment.name }}</v-list-tile-title>
                  <v-list-tile-sub-title>{{ comment.content }}</v-list-tile-sub-title>
                </v-list-tile-content>
              </v-list-tile>
            </v-list>
          </v-card>
        </v-expansion-panel-content>
      </v-expansion-panel>
    </v-card>

    <v-dialog v-model="dialog" max-width="600px">
      <v-card>
        <v-card-title>
          <span class="headline">Comentar</span>
        </v-card-title>
        <v-card-text>
          <v-form>
            <v-text-field label="Nome" v-model="name" placeholder="Seu nome completo"/>
            <v-textarea label="Comentario" v-model="content" placeholder="Escreva seu comentario"/>
          </v-form>
        </v-card-text>
        <v-card-actions>
          <v-spacer></v-spacer>
          <v-btn color="blue darken-1" flat @click="dialog = false">Fechar</v-btn>
          <v-btn color="primary" outline @click="comment()">Comentar</v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>
  </div>
</template>

<script>
export default {
  props: ['post'],
  data () {
    return {
      name: '',
      content: '',
      dialog: false
    }
  },
  methods: {
    like () {
      let posts = JSON.parse(localStorage.getItem('dbSaulloBretas'))

      posts.forEach((element) => {
        if (element.id == this.post.id) {
          this.post.liked = true
          this.post.likesCount++
          element.liked = true
          element.likesCount++
        }
      })

      localStorage.setItem('dbSaulloBretas', JSON.stringify(posts))
    },
    unlike () {
      let posts = JSON.parse(localStorage.getItem('dbSaulloBretas'))

      posts.forEach((element) => {
        if (element.id == this.post.id) {
          this.post.liked = false
          this.post.likesCount--
          element.liked = false
          element.likesCount--
        }
      })

      localStorage.setItem('dbSaulloBretas', JSON.stringify(posts))
    },
    comment () {
      let posts = JSON.parse(localStorage.getItem('dbSaulloBretas'))

      posts.forEach((element) => {
        if (element.id == this.post.id) {
          let comments = element.comments
          let id = comments.length
          let comment = {
            id: id,
            content: this.content,
            name: this.name
          }
          element.comments.unshift(comment)
          this.post.comments.unshift(comment)
          this.content = ''
          this.name = ''
          this.dialog = false
        }
      })

      localStorage.setItem('dbSaulloBretas', JSON.stringify(posts))
    }
  }
}
</script>

<style>

</style>
