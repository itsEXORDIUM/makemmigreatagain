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
        <span v-if="bloc == 'formation'">
          <Formation/>
        </span>
        <span v-if="bloc == 'stageetranger'">
          <StageEtranger/>
        </span>
        <span v-if="bloc == 'communaute'">
          <Communaute/>
        </span>
      </h2>
      <p v-if="texte" v-html="texte"></p>
      <nuxt-link v-if="lien" :to="`/${link}`" class="action big">En savoir plus</nuxt-link>
      <nuxt-link v-if="bloc == 'rejoindre' || bloc == 'formation'" to="/postuler" class="action big">Postuler</nuxt-link>
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
import Formation from '~/components/titres/formation'
import StageEtranger from '~/components/titres/stageetranger'
import Communaute from '~/components/titres/331'

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
    Polyvalents, VoirPays, OnsAppelle, Rejoindre, Formation, StageEtranger, Communaute
  },
  data() {
    return {
      bloc: '',
      link: ''
    }
  },
  mounted() {
    this.checkLien();
    this.checkBloc();
  },
  created() {
    
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
      } else if (this.name =='formation') {
        this.bloc = 'formation';
      } else if (this.name =='stageetranger') {
        this.bloc = 'stageetranger';
      } else if (this.name =='communaute') {
        this.bloc = 'communaute';
      }
    },
    checkLien: function() {
      if(this.lien) {
        console.log(this.lien);
        if(this.lien.includes('formation')) {
          this.link = 'formation';
        } else if(this.lien.includes('mobilite')) {
          this.link = 'mobilite';
        } else if(this.lien.includes('contact')) {
          this.link = 'contact';
        } else if(this.lien.includes('postuler')) {
          this.link = 'postuler';
        }
      }
    }
  }
}
</script>