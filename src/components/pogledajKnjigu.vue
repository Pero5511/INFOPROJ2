<template>
  <v-container>
    <v-card 
    dark
    class="mx-auto"
    max-width="490"
    outlined
  >
    <v-list-item three-line>
      <v-list-item-content>
        <div style="color:orange" align="left" class="text-overline mb-4">
          Knjiga 
        </div>
        <br>
        <v-list-item-title class="text-h5 mb-7">
          {{nazivKnjige}}
        </v-list-item-title>
        <hr>
        <v-list-item-subtitle class="mb-7 mt-7">{{podnaslovKnjige}}</v-list-item-subtitle>
        <br>
        <v-list-item-subtitle style="color:orange" align="left">Autori:</v-list-item-subtitle>
        <v-list-item-subtitle class="mb-7" v-for="autor in autori" :key=autor>{{autor}}</v-list-item-subtitle>
        <v-list-item-subtitle style="color:orange" align="left">Stranica: </v-list-item-subtitle>
        <v-list-item-subtitle>{{brStr}}</v-list-item-subtitle>
        <v-list-item-subtitle style="color:orange" align="left">Godina izdavanja: </v-list-item-subtitle>
        <v-list-item-subtitle>{{godIzd}}</v-list-item-subtitle>
        <a target=”_blank” align="right" style="text-decoration:none" :href=id><v-btn class="mt-3" outlined color="orange">VIŠE ></v-btn></a>
        <br>
      </v-list-item-content>
    </v-list-item>
  </v-card>
  </v-container>
</template>

<script>
  export default {
    name: 'pogledajKnjigu',
    props: ['nazivKnjige','podnaslovKnjige','id','autori','brStr','godIzd'],

    data: () => ({
    }),
  }
</script>
