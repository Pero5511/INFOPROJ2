<template style="background:#000000">
  <v-app style="
  background: #3A1C71;
  background: -webkit-linear-gradient(to right, #FFAF7B, #D76D77, #3A1C71);
  background: linear-gradient(to right, #FFAF7B, #D76D77, #3A1C71);
"><v-container>
    <v-row>
    <v-col>
    <v-app-bar
      app
      shrink-on-scroll
      color="black"
      flat
    >
     
      <v-avatar
        class="hidden-sm-and-down"
        color="grey darken-1 shrink"
        size="32"
      ></v-avatar>
    </v-app-bar></v-col><v-col>
    <v-app-bar src="@/img/carbon-fiber-texture-linear-gradient-260nw-1316111075.jpg"
    dark
      app
      shrink-on-scroll
    >
    <v-img class="hidden-sm-and-down" shrink-on-scroll src="@/img/pngwing.com.png" max-height="60"
  max-width="60"></v-img>
    <v-col><v-toolbar-title class="hidden-sm-and-down orange--text">E-Books</v-toolbar-title></v-col>
      <v-tabs
        centered
        class="mr-0"
        color="orange darken-1"
        show-arrows
      >
        <v-tab
          v-for="[ikona,ruta] in links"
          :key="ikona"
          :to="ruta"
        ><v-icon large color="orange darken-4">{{ikona}}</v-icon>
        </v-tab>
      </v-tabs>
    </v-app-bar></v-col></v-row></v-container>

      <v-container style="background-color:black" class="pt-14 mt-14">
        <router-view></router-view>
        <br><br><br>
        <hr class="ma-4">
        <p align="center">Powered by Logovita, QOTD and Google Books APIs.</p>
        <p align="center">Created By Perica Topić - 2022</p>
      </v-container>
    
  </v-app>
</template>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #ff9950;
}

nav {
  padding: 30px;

  a {
    font-weight: bold;
    color: #2c3e50;

    &.router-link-exact-active {
      color: #42b983;
    }
  }
}
</style>

<script>
  export default {
    data: () => ({
      links: [
        ["mdi-book-open-variant","/"],
        ["mdi-magnify","/pretraga"],
        ["mdi-cart-outline","/shop"],
        ["mdi-cards-heart-outline","/pretplata"],
        ["mdi-account-supervisor","/about"],
      ],
    }),
  }
</script>
