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
        <span v-if="bloc == 'frigo'">
          <Frigo/>
        </span>
        <span v-if="bloc == 'espacepro'">
          <EspacePro/>
        </span>
        <span v-if="bloc == 'adoptalt'">
          <AdoptAlt/>
        </span>
        <span v-if="bloc == 'unprojet'">
          <UnProjet/>
        </span>
      </h2>
      <p v-if="texte" v-html="texte"></p>
      <nuxt-link v-if="lien && bloc != 'espacepro' && bloc != 'adoptalt' && bloc != 'unprojet'" :to="`/${link}`" class="action big">En savoir plus</nuxt-link>
      <nuxt-link v-if="bloc == 'rejoindre' || bloc == 'formation'" to="/postuler" class="action big">Postuler</nuxt-link>
      <a :href="lien" title="Déposer une offre (Nouvelle fenêtre)" target="_blank" v-if="bloc == 'espacepro'" to="/" class="action big">Déposer une offre</a>
      <a :href="lien" title="Adoptez un alternant (Nouvelle fenêtre)" target="_blank" v-if="bloc == 'adoptalt'" to="/" class="action big">Adoptez un apprenti</a>
      <a :href="lien" title="Proposez un projet (Nouvelle fenêtre)" target="_blank" v-if="bloc == 'unprojet'" to="/" class="action big">Proposer un projet</a>
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
import Frigo from '~/components/titres/frigo'
import EspacePro from '~/components/titres/espacepro'
import AdoptAlt from '~/components/titres/adoptalt'
import UnProjet from '~/components/titres/unprojet'

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
    Polyvalents, VoirPays, OnsAppelle, Rejoindre, Formation, StageEtranger, Communaute, Frigo, EspacePro, AdoptAlt, UnProjet
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
      } else if (this.name =='frigo') {
        this.bloc = 'frigo';
      } else if (this.name =='espacepro') {
        this.bloc = 'espacepro';
      } else if (this.name =='adoptalt') {
        this.bloc = 'adoptalt';
      } else if (this.name =='unprojet') {
        this.bloc = 'unprojet';
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