<script>
import {useCatsStore} from "@/stores/cats.js";
import CatsList from "@/components/CatsList.vue";
export default {
  name: "CatsView",
  components: {CatsList},
  data(){
    return{
      catsStore: useCatsStore()
    }
  },
  computed:{
    catsListTitle(){
      return  'Een gemiddelde kat kost ' + this.catsStore.averagePrice + ' euro';
    }
  },
  methods:{
    handleAdoptClick(cat){

      const index = this.catsStore.cats.indexOf(cat)
      this.catsStore.cats.splice(index, 1)
    }
  }
}


</script>

<template>
<cats-list @adopt-clicked="handleAdoptClick" :title="catsListTitle" :cats="catsStore.cats"/>
</template>

<style scoped>

</style>