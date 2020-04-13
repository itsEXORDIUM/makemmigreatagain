<template>
  <div class="bloc_home">
      <h2>{{titre}}</h2>
      <p>{{texte}}</p>
      <nuxt-link :to="lien">En savoir plus</nuxt-link>
      <div v-for="(img, index) in images" :key="index">
          <img :src="img" alt=""/>
      </div>
  </div>
</template>

<script>
export default {
  props: {
      titre: '',
      texte: '',
      lien: '',
      images: []
  }
}
</script>