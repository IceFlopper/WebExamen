<script>
import {useCatsStore} from "@/stores/cats.js";

export default {
  name: "CatsList",

  props:{
    title: String,
    cats: Array
  },
  methods:{
    handleAdoptClick(cat){
      this.$emit('adoptClicked', cat);
    }
  }


}

</script>

<template>
  <div>
    <h1>{{ title }}</h1>
    <div v-for="(cat, index) in cats" :key="index + cat.name" class="cat-list">
      <img class="cat-image" :src="'/src/assets/' + cat.imgPath" :alt="cat.name">
      <div class="text-container">
        <h1>dit is een {{cat.name}}</h1>
        <h1 id="cat-price-text">hij kost {{cat.price}}</h1>
        <input @click="handleAdoptClick(cat)" type="button" value="Adopt me! ก₍⸍⸌̣ʷ̣̫⸍̣⸌₎ค">
      </div>

    </div>
  </div>
</template>

<style scoped>
.cat-list{
  display: flex;
  flex-direction: row;
  margin: 20px;
  align-items: center;
}
.cat-list *{
  margin: 5px;
}
#cat-price-text{
  color: red;
}
.cat-image{
  width: 150px;
}
.text-container{
  display: flex;
  flex-direction: column;
  align-items: start;
  justify-content: center;
}
</style>