<template>
  <div class="home">
    <v-row><v-col xs="12" sm="12" md="6" lg="6" xl="6">
    <h1 align="left" class="pa-10">Dobrodošli na E-BookStore !</h1></v-col><v-col xs="12" sm="12" md="6" lg="6" xl="6"><v-btn class="ma-12 mr-1" outlined to=/pretraga color="orange">PRETRAŽI >>></v-btn></v-col>
    </v-row>
    <h1 class=" pa-10 orange--text" align="left">Najpopularnije > </h1>
    <v-carousel class="mb-10" max-width="300" align="center" :show-arrows="true" cycle interval="4500">
    <a href="http://www.logovita.ba/"><v-carousel-item
      v-for="(item,i) in items"
      :key="i"
      :src="item.src"
    ></v-carousel-item></a>
  </v-carousel>
  <v-row><v-col align="center">
    <h1 class=" pa-10 orange--text" align="left">Odabrani citat:</h1><br><br>
<v-sheet
  rounded
  class="mx-16 pa-10"
  color="orange"
  elevation="1"
  height=auto
  width="auto"
><h2>"{{comp}}"</h2></v-sheet>
    </v-col></v-row>
  <h1 class=" pa-10 orange--text" align="left">Urednici odabrali:</h1>
  <v-container><v-row>
    <v-col xs="12" sm="12" md="6" lg="6" xl="6" ><a href="http://www.logovita.ba/klasicni-i-suvremeni-roman/3930-harry-potter-i-ukleto-dijete-9789533168302.html"><img style="max-width:295px" src="@/img/29056083.jpg"></a>
    </v-col>
    <v-col xs="12" sm="12" md="6" lg="6" xl="6"><h2 class="pt-16 mt-16">Harry Potter i ukleto dijete</h2><hr>
    <p>Opis: Harryju Potteru nikad nije bilo lako pa nije ni danas dok nastoji pronaći ravnotežu između uloga prezaposlenog djelatnika Ministarstva magije, supruga i oca troje djece školske dobi. I dok je Harry prisiljen uhvatiti se ukoštac s prošlošću koja odbija ostati gdje joj je i mjesto, njegov najmlađi sin Albus mora se boriti s teretom obiteljskog nasljeđa koje nikad nije želio...</p>
    </v-col></v-row>
    <v-row><v-col xs="12" sm="12" md="6" lg="6" xl="6"><a href="http://www.logovita.ba/klasicni-i-suvremeni-roman/8050-rijeka-svjetla-i-tame-9789533604114.html"><img style="max-width:295px" src="@/img/rijeka-svjetla-i-tame.jpg">
    </a></v-col>
    <v-col xs="12" sm="12" md="6" lg="6" xl="6"><h2 class="pt-16 mt-16">Rijeka svjetla i tame</h2><hr>
    <p>Opis: Ispričan iz dvije vremenske perspektive, roman Rijeka svjetla i tame naizmjenično prati policijski slučaj i djetinjstvo sestara, dok čitatelju jednako tako naizmjenično ubrzava puls i slama srce. No to je ujedno i portret jednoga grada i društva u krizi oslikan kroz priču o sestrinstvu, ovisnosti i neraskidivim vezama koje postoje između mjesta, obitelji i sudbine.  </p>
    </v-col>
    </v-row>
    <v-row><v-col xs="12" sm="12" md="6" lg="6" xl="6"><a href="http://www.logovita.ba/klasicni-i-suvremeni-roman/7991-palaca-od-papira-9789533604060.html"><img style="max-width:295px" src="@/img/palaca-od-papira.jpg">
    </a></v-col>
    <v-col xs="12" sm="12" md="6" lg="6" xl="6"><h2 class="pt-16 mt-16">Palača od papira</h2><hr>
    <p>Opis: "Duboko emotivna ljubavna priča… u kojoj se otkrivaju tajne, laži i vrlo zamršen ljubavni trokut." - Reese Witherspoon  </p>
    </v-col>
    </v-row></v-container>
  </div>
</template>

<script>
export default {
  data () {
      return {
        comp:[],
        items: [
          {
            src: require("@/img/6149fa5fde0e7b00194b9264.jpg"),
          },
          {
            src: require("@/img/best-books-of-2019-1568659903.jpg"),
          },
          {
            src: require("@/img/619bbeff1ca92500180c3b27.jpg"),
          },
          {
            src: require("@/img/cover2-9d5a07ec570aa8f7d7a26b865379d5eff4597729-s800-c85.jpg"),
          },
          {
            src: require("@/img/sm_f7e651-tolkien-lordoftherings.jpg"),
          },
          {
            src: require("@/img/The-Hobbit-book-cover.jpg"),
          },
        ],
      }
    },
  name: 'HomeView',
  components: {
  },
      mounted: function(){
        this.axios.get('https://favqs.com/api/qotd')
        .then(response=>{
          console.log(response.data.quote.body)
          this.comp=response.data.quote.body
        })
      }
  
}
</script>
