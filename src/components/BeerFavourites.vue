<template>
<div class="fav-container" v-if="beer">
    <h1>Favourites</h1>
  <ul>
      <li v-for="(beer, index) in beer" :beer="beer" :key="index">{{beer}}</li>
    </ul>
</div>
</template>

<script>
import BeerDetail from './BeerDetail.vue';

export default {
    name: 'fav-beers',
    props: ['beer'],
    components:{
        "beer-detail" :BeerDetail
    }

}
</script>

<style scoped>
.fav-container{background-color: #27292D;
                        color: #EEEEEE;
                        border-style: none;
                        border-radius: 12px;
                        padding: 2%;
                        text-align: center;
                        margin: 2%;}
ul {
  list-style-type: none;
 }

h1{color: #E27C22;}
</style>

