<template>
  <div class="main-container">
  <h1>Brewdog Beers</h1>
  <beers-list :beers='beers'></beers-list>
  <beer-detail :beer="selectedBeer"></beer-detail>
  <fav-beers :beer="favBeers"></fav-beers>
  </div>
</template>

<script>
import BeersList from './components/BeerList.vue';
import BeerDetail from './components/BeerDetail.vue';
import BeerFavourites from './components/BeerFavourites.vue';
import { eventBus } from './main.js';

export default {
  name: 'app',
  data(){
    return {
      beers: [],
      selectedBeer: null,
      favBeers: []
    };
  },
  mounted(){
    fetch('https://api.punkapi.com/v2/beers')
    .then(result => result.json())
    .then(beers => this.beers = beers)

    eventBus.$on('beer-selected', (beer) => {
      this.selectedBeer = beer
    })

    eventBus.$on('favourited-beer', (beer) => {
      this.favBeers.push(beer)
    })
  },
  components: {
    "beers-list": BeersList,
    "beer-detail": BeerDetail,
    "fav-beers": BeerFavourites
  },
  computed(){
    addBeerToFavs = function(){
    this.favBeers.push(selectedBeer)      
    }
  }
}
</script>


<style scoped>
.main-container{background-color: #161C20;
                padding: 4%;
                font-family: 'Roboto Slab', serif;}
h1{text-align: center;
  font-size: 3em;
  color: #eeeeee;}
  


                
</style>