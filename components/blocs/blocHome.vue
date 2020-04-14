<template>
  <div class="bloc_home">
      <h2>{{titre}}</h2>
      <p v-if="texte">{{texte}}</p>
      <nuxt-link v-if="lien" :to="lien">En savoir plus</nuxt-link>
      <img v-for="(img, index) in images" :key="index" :src="img" alt=""/>
      <img v-if="image" :src="image" alt=""/>
  </div>
</template>

<script>
export default {
  props: {
      titre: '',
      texte: '',
      lien: '',
      images: Array,
      image: ''
  }
}
</script>