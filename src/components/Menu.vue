<template>
  <div>
    <v-card>
      <v-card-title primary-title>
        <div>
          <h3 class="headline mb-0">Menu</h3>
        </div>
      </v-card-title>

      <v-list>
        <v-list-tile to="/">
          <v-list-tile-content>
            <v-list-tile-title>Inicio</v-list-tile-title>
          </v-list-tile-content>
        </v-list-tile>
        <v-list-tile to="/create">
          <v-list-tile-content>
            <v-list-tile-title>Criar postagem</v-list-tile-title>
          </v-list-tile-content>
        </v-list-tile>
      </v-list>
    </v-card>
    <v-card class="mt-3">
      <v-card-title primary-title>
        <div>
          <h3 class="headline mb-0">Sobre</h3>
        </div>
      </v-card-title>

      <v-list>
        <v-list-tile href="https://github.com/saullo/blog-diw" avatar>
          <v-list-tile-content>
            <v-list-tile-title>Github</v-list-tile-title>
            <v-list-tile-sub-title>Visite o repositorio do projeto</v-list-tile-sub-title>
          </v-list-tile-content>
        </v-list-tile>
      </v-list>
    </v-card>
  </div>
</template>

<script>
export default {

}
</script>

<style>

</style>
