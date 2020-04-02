<template>
<div class="detail-container" v-if='beer'>
  <h1>{{beer.name}}</h1>
  <h2>Tagline</h2>
  <p>{{beer.tagline}}</p>
  <h2>Description:</h2>
  <p>{{beer.description}}</p>
  <h2>Food Pairing</h2>
  <p v-for="(pairing, index) in beer.food_pairing" :beer="beer" :key="index" >{{pairing}}</p>
  <button v-on:click="handleButton">Add To Favourites</button>
  <div class="img-container"><img :src="beer.image_url" alt="A BEER!"></div>
  
  
</div>
</template>

<script>
import { eventBus } from '../main.js';

export default {
    name: 'beer-detail',
    props: ['beer'],
    methods: {
        handleButton(){
            eventBus.$emit('favourited-beer', this.beer.name)
        }
    }

}
</script>

<style scoped>
    .detail-container{ background-color: #27292D;
                        color: #EEEEEE;
                        border-style: none;
                        border-radius: 12px;
                        padding: 2%;
                        text-align: center;
                        }
    h2{color: #2A73C1;}

    button { background-color: #2A73C1;
            color: #EEEEEE;
            border-style: solid 4px;
            border-color:  #2A73C1;
            border-radius: 12px;
            font-size: 1em;
            font-family: 'Roboto Slab', serif;}
    button:hover {background-color: #27292D;
                color: #2A73C1;
                transition: 0.6s;
                }

    h1{color: #2A73C1;}
    img{height: 10%;
        width: 10%;
        position: relative;
        left:35%;
        bottom: 180px;}
    /* .img-container{
        position: relative;
        left: 40%;
        top: 10px;
        } */
</style>
