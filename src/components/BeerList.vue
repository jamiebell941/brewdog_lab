<template>
<div class="list-container">
  <h1>Beers List</h1>
  <details>
      <summary>Select a beer</summary>
      <ul>
      <list-item v-for="(beer, index) in beers" :beer="beer" :key="index"></list-item>
  </ul></details>
  <!-- <label for="beers-list">Choose a beer</label> -->
  <!-- <list-item>
      <select name="beers-list" id="beers-list">
    <option disabled value="">Select a beer</option>
    <option v-for="(beer, index) in beers" :beer="beer" :key="index">{{beer.name}} </option>
  </select>
  </list-item> -->
</div>
</template>

<script>
import ListItem from './BeerListItem.vue';

export default {
    name: 'beers-list',
    props: ['beers'],
    components: {
        "list-item": ListItem
    }

}
</script>

<style scoped>
    .list-container{background-color: #27292D;
                        color: #EEEEEE;
                        border-style: none;
                        border-radius: 12px;
                        padding: 2%;
                        text-align: center;
                        margin: 2%;}
    ul {
  list-style-type: none;
  text-align: center;
  padding: 10px;
 }
 h1{color:#3DC642}
 summary {color: #eeeeee;}
</style>