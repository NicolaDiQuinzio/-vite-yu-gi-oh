<template>
  <header>
   <AppHeader/>
  </header>
  <main>
    <Cards/>
   
  </main>
</template>

<script >

import AppHeader from './components/AppHeader.vue'
import Cards from './components/Cards.vue';
import axios from 'axios';
import { store } from './data/data';
export default {
  name:'App',
  components: {
    AppHeader,
    Cards
},
data () {

  return{

  store}
},
methods: {
      getCharachters () {
        const Api = store.Url + store.endPoint;
        axios.get(Api).then((res) => {
          store.cardList = res.data.data
          
        })
      }
    },
    mounted(){
      store.endPoint= 'v7/cardinfo.php?num=50&offset=0'
    this.getCharachters();
  }
}

</script>


<style lang="scss" scoped>

main{
  background-color:#d48f38 ;
}
</style>
