<template>
  <div class="search"><v-row><v-col>
    <h1 class="pa-5">SHOP</h1></v-col><v-col>
      <a style="text-decoration:none" href="#kosarica"><v-btn v-if="kupnja" class="mt-6" outlined color="orange">KOŠARICA ></v-btn></a>
      </v-col></v-row>
    <v-container style="background-color:orange">
    <v-row class=""><v-col xs="12" sm="5" md="5" lg="5" xl="5"><img max-width=115 max height=115 src="@/img/book-png.png"></v-col>
    <v-col xs="12" sm="7" md="7" lg="7" xl="7"><v-text-field class="mt-12" color=black large label="Unesite naziv knjige koju želite kupiti..." v-model="pretraga" @keydown.enter="novisearch()"></v-text-field></v-col></v-row>
    <h4 align="left" v-if="rezult" style="color:black">Pronađeno: {{brrez}}</h4>
    </v-container>
    <v-container>
    <v-row>
      <v-col xs="12" sm="6" md="6" lg="6" xl="4" v-for="item in apiweb" :key="item.id">
        <a @click="kupi(item.volumeInfo.title)"><kupi-knjigu :nazivKnjige="item.volumeInfo.title"></kupi-knjigu></a>
                </v-col>
              </v-row></v-container>
    
    <v-pagination v-if="rezult" dark @input="dohvatiAPI()"
      color="orange"
      v-model="stranica"
      :length="Math.floor(this.comp.totalItems/12)"
    ></v-pagination>
    <v-snackbar
      color="success"
      v-model="snack"
      :timeout="timeout"
    >
      <h3 class="pa-7" align="center">Uspješno kupljeno!!</h3>
    </v-snackbar>
    <v-container id="kosarica" v-if="kupnja"><br><br><br><hr>
      <h2 class="ma-10">Vaša košarica:</h2><hr><br><br>
      <v-row class="pl-4 pb-3"><v-col v-for="item in kupljeno" :key="item">
        <v-card align="center" max-width="150" max-height="100" color="orange"><p class="ma-7" align="center">{{item}}</p></v-card>
        </v-col></v-row>
      <v-btn @click="kosaraKupi()" v-if="kupnja" class="mt-6" outlined color="orange">KUPI ></v-btn>
</v-container>
  </div>
</template>



<script>
// @ is an alias to /src
import kupiKnjigu from '@/components/kupiKnjigu.vue'

export default {
  data: () => ({
    pretraga:"",
    stranica:1,
    apiweb:[],
    comp:[],
    rezult:false,
    kupnja:false,
    brrez:0,
    kupljeno:[],
    snack:false,
    timeout:3000,
  }),
  name: 'HomeView',
  components: {
    kupiKnjigu
  },
  methods:{
      kosaraKupi: function(){
        this.snack=true
        this.kupljeno=[]
        this.kupnja=false
      },
      kupi: function(argument){
        this.kupljeno.push(argument)
        this.kupnja=true
      },
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
