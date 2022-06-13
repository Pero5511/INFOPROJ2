<template>
  <div class="home">
    <h2 class="pa-14">Pretplatite se na naš besplatni Newsletter!</h2>
    <v-form style="background-color:#ffa06e;color:#000000;">
    <v-container>
      <v-row>
        <v-col 
          cols="12"
          sm="12"
          md="6"
        >
          <v-text-field
            color=black
            label="Ime"
            placeholder="Unesite ime ovdje..."
          ></v-text-field>
        </v-col>

        <v-col
          cols="12"
          sm="12"
          md="6"
        >
          <v-text-field
            color=black
            label="Prezime"
            placeholder="Unesite prezime ovdje..."
          ></v-text-field>
        </v-col></v-row>
        <v-row><v-text-field class="pa-3"
            color=black
            label="E-mail"
            placeholder="Unesite vaš e-mail ovdje..."
          ></v-text-field></v-row>
        <v-row>
          <v-checkbox class="pa-12"
          v-model="checkbox"
          label="Slažem se s odredbama međunarodnog ugovora o internetskom oglašavanju."
    ></v-checkbox></v-row>
    <v-row align="center">
        <v-col><v-btn v-if="checkbox" align="center" class="text-center ma-2"
      dark
      @click="snackbar = true"
    >
      Potvrdi
    </v-btn>
        </v-col></v-row></v-container></v-form>
    <v-snackbar
      v-model="snackbar"
    >
      {{ text }}

      <template v-slot:action="{ attrs }">
        <v-btn
          color="success"
          text
          v-bind="attrs"
          @click="snackbar = false"
        >
          X
        </v-btn>
      </template>
    </v-snackbar>
  </div>
</template>

<script>
// @ is an alias to /src
//import HelloWorld from '@/components/HelloWorld.vue'

export default {
  data () {
      return {
        checkbox: false,
        snackbar: false,
        text: "Zahvaljujemo se na pretplati!",
      }
    },
  name: 'HomeView',
  components: {
    
  }
}
</script>
