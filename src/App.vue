<template>
  <div>
    <v-app>
      <v-container grid-list-xl>
        <v-layout row wrap justify-center>
          <v-flex xs12 sm md lg10 xl8>
           <h1 class="display-3 font-weight-bold mb-4"><router-link to="/" style="text-decoration:none">Blog</router-link></h1> 
           <v-divider/>
          </v-flex>
        </v-layout>
        <v-layout row wrap justify-center>
          <v-flex class="hidden-sm-and-up" xs12 sm4 xl3>
            <Menu/>
          </v-flex>
          <v-flex xs12 sm8 lg6 xl5>
            <router-view/>
          </v-flex>
          <v-flex xs12 sm4 xl3 class="hidden-xs-only">
            <Menu/>
          </v-flex>
        </v-layout>
      </v-container>
    </v-app>
  </div>
</template>

<script>
import Menu from '@/components/Menu'

export default {
  components: {
    Menu
  },
  mounted () {
    this.init()
  },
  methods: {
    init () {
      let posts = localStorage.getItem('dbSaulloBretas')
      if (!posts) {
        let posts = []
        let date = new Date()
        let year = date.getFullYear()
        let month = date.getMonth() + 1
        let day = date.getDate()
        let fullDate = `${day}/${month}/${year}`
        for (let i = 0;i < 5;i++) {
          let post = {
            id: i,
            title: 'Lorem ipsum dolor sit amet consectetur adipisicing elit. Debitis, neque.',
            content: 'Lorem ipsum dolor sit amet consectetur adipisicing elit. Asperiores facere magni autem, corrupti enim in beatae voluptates hic sed at reprehenderit dolorem numquam, totam minima odio tenetur sapiente ab officia nam officiis nemo! Molestias pariatur commodi dolor voluptas placeat corrupti tempore, rem minus! Inventore ratione, laudantium veritatis laborum in, ipsam vitae necessitatibus maxime provident reprehenderit dolores neque temporibus aspernatur nam voluptas. Mollitia esse unde temporibus incidunt modi explicabo. Corporis molestiae iste officiis culpa alias, doloribus optio veritatis exercitationem explicabo. Culpa maiores voluptas blanditiis deserunt consequuntur exercitationem, perspiciatis aliquam recusandae impedit atque quibusdam doloribus placeat autem vitae incidunt earum ullam quia architecto doloremque esse. Magni voluptatem hic, consequuntur blanditiis ratione nobis molestias eum laborum perferendis. Doloribus, ducimus repudiandae, quae itaque accusantium, quisquam deserunt a quod nemo earum beatae fugiat aperiam qui officiis nesciunt odit. Laudantium debitis doloribus voluptatum mollitia consequuntur rerum, esse veniam deleniti quidem dolores maxime nobis neque eos facilis eius, autem fugiat provident, praesentium aliquam reprehenderit excepturi similique! Sed sapiente repellendus, itaque culpa exercitationem at libero ipsa. Laborum, dolorum mollitia minus itaque adipisci illum aperiam porro dignissimos debitis delectus iste quia corrupti maiores quos, qui dolore ab, repudiandae est deleniti! Voluptatem dolores minima dolorum voluptas neque asperiores distinctio nisi.',
            likesCount: 0,
            commentsCount: 0,
            liked: false,
            comments: [],
            date: fullDate
          }
          posts.unshift(post)
        }
        localStorage.setItem('dbSaulloBretas', JSON.stringify(posts))
      }
    }
  }
}
</script>

<style>

</style>
