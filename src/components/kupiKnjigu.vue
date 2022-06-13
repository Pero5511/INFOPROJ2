<template>
  <v-container>
    <v-card 
    dark
    class="mx-auto"
    max-width="1000"
    outlined
  >
    <v-list-item three-line>
      <v-list-item-content>
        <div style="color:orange" align="left" class="text-overline">
          Knjiga 
        </div>
        <v-row><v-col cols="7">
        <v-list-item-title class="text-h5">
          {{nazivKnjige}}
        </v-list-item-title></v-col><v-col cols="5">
        <v-btn outlined color="orange">KUPI ></v-btn></v-col></v-row>
        <br>
      </v-list-item-content>
    </v-list-item>
  </v-card>
  </v-container>
</template>

<script>
  export default {
    name: 'kupiKnjigu',
    props: ['nazivKnjige'],

    data: () => ({
    }),
  }
</script>
