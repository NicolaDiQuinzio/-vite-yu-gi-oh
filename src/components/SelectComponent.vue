<template>
  
  <div class="row p-5">
        <div class="col d-flex justify-content-center ">
        <form class="d-flex w-50"> 
            <div class="me-2">
                <input type="text" class="form-control" id="cardname" placeholder="Search name" v-model.trim="store.search.name">
            </div>
            <select class="form-select me-2" id="searchArchetype" v-model="store.search.archetype">
            <option selected value="">Choose</option>
            <option :value="archetype" v-for="(archetype, index) in archetypeOptions" :key="index">{{ archetype.archetype_name }}</option>
            </select>
            <div>
                <button type="submit" class="btn btn-primary">Search</button>
            </div>
        </form>
        </div>
  </div>
</template>

<script>
import axios from 'axios';
import { store } from '../data/data';
export default {

    name: 'SelectComponent',
    data() {
        return {
            store,
            archetypeOptions: []
        }
    },
    methods: {
        setSearch() {
            this.$emit('searchChange');
        }
    },

    mounted() {
        axios.get('https://db.ygoprodeck.com/api/v7/archetypes.php').then((res) => {
            this.archetypeOptions = res.data
            
        })
    }
}
</script>


<style lang="scss" scoped>

</style>