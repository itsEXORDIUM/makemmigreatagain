<template>
  <div :class="`bloc_home wrap ${name}`">
    <div>
       <h2 class="bloc_titre">
        <span class="show-for-sr">{{titre}}</span>
        <span v-if="bloc == 'polyvalents'">
          <Polyvalents/>
        </span>
      </h2>
      <p v-if="texte">{{texte}}</p>
      <nuxt-link v-if="lien" :to="lien" class="action big">En savoir plus</nuxt-link>
    </div>
    <div>
      <img v-for="(img, index) in images" :key="index" :src="img" alt=""/>
      <img v-if="image" :src="image" alt=""/>
    </div>
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
  data() {
    return {
      bloc: ''
    }
  },
  mounted() {
    this.checkBloc();
  },
  methods: {
    checkBloc: function() {
      if(this.name == 'polyvalents') {
        this.bloc = 'polyvalents';
      }
    }
  }
}
</script>