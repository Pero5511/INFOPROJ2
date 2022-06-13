<template>
  <div class="search">
    <h1 class="pa-5">Pronađite vašu omiljenu knjigu...</h1>
    <v-container style="background-color:orange">
    <v-row class="ma-2"><v-col xs="12" sm="12" md="6" lg="6" xl="6"><img max-width=190 max height=190 src="@/img/ab8ad03b5beb5a93fe0b512bf48bb314.png"></v-col>
    <v-col xs="12" sm="12" md="6" lg="6" xl="6"><v-text-field class="mt-12" color=black large label="Pretraga..." v-model="pretraga" @keydown.enter="novisearch()"></v-text-field></v-col></v-row>
    <h3 align="center" v-if="rezult" style="color:black">Pronađeno {{brrez}} rezultata!</h3>
    </v-container>
    <v-container>
    <v-row>
      <v-col xs="12" sm="6" md="6" lg="4" xl="3" v-for="item in apiweb" :key="item.id">
        <pogledaj-knjigu :nazivKnjige="item.volumeInfo.title" :podnaslovKnjige="item.volumeInfo.subtitle"
        :autori="item.volumeInfo.authors" :brStr="item.volumeInfo.pageCount" :godIzd="item.volumeInfo.publishedDate" :id="item.volumeInfo.infoLink"></pogledaj-knjigu>
                </v-col>
              </v-row></v-container>
    
    <v-pagination v-if="rezult" dark @input="dohvatiAPI()"
      color="orange"
      v-model="stranica"
      :length="Math.floor(this.comp.totalItems/12)"
    ></v-pagination>
  </div>
</template>


<script>
// @ is an alias to /src
import pogledajKnjigu from '@/components/pogledajKnjigu.vue'

export default {
  data: () => ({
    pretraga:"",
    stranica:1,
    apiweb:[],
    comp:[],
    rezult:false,
    brrez:0,
  }),
  name: 'HomeView',
  components: {
    pogledajKnjigu
  },
  methods:{
      novisearch: function(){
        this.dohvatiAPI()
        this.stranica=1
      },
      dohvatiAPI: function(){
        this.axios.get('https://www.googleapis.com/books/v1/volumes?q=' + this.pretraga + '&maxResults=12&startIndex=' + this.stranica)
        .then(response=>{
          console.log(response.data.items)
          this.comp=response.data
          this.apiweb=response.data.items
          this.rezult=true
          this.brrez=this.comp.totalItems
        })
      }
    }
}
</script>
