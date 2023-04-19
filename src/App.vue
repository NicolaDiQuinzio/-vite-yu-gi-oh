<template>
  <header>
   <AppHeader/>
  </header>
  <main>
    <SelectComponent/>
    <Cards/>
   
  </main>
</template>

<script >

import AppHeader from './components/AppHeader.vue'
import SelectComponent from './components/SelectComponent.vue'
import Cards from './components/Cards.vue';
import axios from 'axios';
import { store } from './data/data';
export default {
  name:'App',
  components: {
    AppHeader,
    SelectComponent,
    Cards,
},

data() {

  return {

    store
  }
},
methods: {
  getCharachters() {
    const Api = store.Url + store.endPoint;  
    axios.get(Api).then((res) => {
      store.cardList = res.data.data
      console.log(store.cardList)
    })
  },

  getArchetypes() {
    const URL = store.Url + store.endPoint;
    let options = {}
    let params = {}

    for (let key in store.search) {
      if (store.search[key]) {
        params[key] = store.search[key].archetype_name
      }
    }

    if (Object.keys(params).length > 0) {
      options.params = params;
     
    }
    axios.get(URL, options).then((res) => {
      store.cardList = res.data.data
    })
  }
},
mounted() {
  store.endPoint = 'v7/cardinfo.php?num=50&offset=0';
  this.getCharachters();
}
}

</script>


<style lang="scss" scoped>

main{
  background-color:#d48f38 ;
}
</style>







/*
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

    getSelectComponent(){
      const URL=store.Url + store.endPoint;
      let options={}
      let params={}
      for(let key in store.search){
        if (store.search[key]){

        }
      }

      if(Object.keys(params).length>0){
        options.params= params;
      }

      axios.get(URL, options).then((res)=>{
      store.cardList=res.data.data
      })
    },

    mounted(){
     store.endPoint= 'v7/cardinfo.php?num=50&offset=0'
    this.getCharachters();
  }
}*/