<template>
  <div :class="`bloc_home wrap ${name}`">
    <div>
       <h2 class="bloc_titre">
        <span class="show-for-sr">{{titre}}</span>
        <span v-if="bloc == 'polyvalents'">
          <Polyvalents/>
        </span>
        <span v-if="bloc == 'pays'">
          <VoirPays/>
        </span>
        <span v-if="bloc == 'contact'">
          <OnsAppelle/>
        </span>
        <span v-if="bloc == 'rejoindre'">
          <Rejoindre/>
        </span>
      </h2>
      <p v-if="texte" v-html="texte"></p>
      <nuxt-link v-if="lien" :to="lien" class="action big">En savoir plus</nuxt-link>
      <nuxt-link v-if="bloc == 'rejoindre'" to="/" class="action big">Postuler</nuxt-link>
    </div>
    <div>
      <img v-for="(img, index) in images" :key="index" :src="img" alt=""/>
      <img v-if="image" :src="image" alt=""/>
    </div>
  </div>
</template>

<script>
import Polyvalents from '~/components/titres/polyvalents'
import VoirPays from '~/components/titres/voirpays'
import OnsAppelle from '~/components/titres/onsappelle'
import Rejoindre from '~/components/titres/rejoindre'

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
    Polyvalents, VoirPays, OnsAppelle, Rejoindre
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
      } else if (this.name =='pays') {
        this.bloc = 'pays';
      } else if (this.name =='contact') {
        this.bloc = 'contact';
      } else if (this.name =='rejoindre') {
        this.bloc = 'rejoindre';
      }
    }
  }
}
</script>