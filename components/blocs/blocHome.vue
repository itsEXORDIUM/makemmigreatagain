<template>
  <div :class="`bloc_home wrap ${name}`">
      <h2 class="bloc_titre">
        <span class="show-for-sr">{{titre}}</span>
        <Polyvalents/>
      </h2>
      <p v-if="texte">{{texte}}</p>
      <nuxt-link v-if="lien" :to="lien" class="action big">En savoir plus</nuxt-link>
      <img v-for="(img, index) in images" :key="index" :src="img" alt=""/>
      <img v-if="image" :src="image" alt=""/>
  </div>
</template>

<script>
import Polyvalents from '~/components/titres/polyvalents'

export default {
  props: {
      name: '',
      titre: '',
      texte: '',
      lien: '',
      images: Array,
      image: ''
  },
  components: {
    Polyvalents
  },
  mounted() {
  }
}
</script>