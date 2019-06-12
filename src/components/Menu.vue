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
  </div>
</template>

<script>
export default {

}
</script>

<style>

</style>
