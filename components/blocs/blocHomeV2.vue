<template>
  <div :class="`bloc_home v2 wrap ${name}`">
    <div class="ligne">
      <div>
        <h2 class="bloc_titre">
          <span class="show-for-sr">{{titre}}</span>
          <span v-if="bloc == 'altini'">
            <Alternanceini/>
          </span>
          <span v-if="bloc == 'departement'">
            <NotreDepartement/>
          </span>
          <span v-if="bloc == 'design'">
            <Design/>
          </span>
          <span v-if="bloc == 'developpement'">
            <Developpement/>
          </span>
          <span v-if="bloc == 'communication'">
            <Communication/>
          </span>
          <span v-if="bloc == 'stagealt'">
            <StageAlt/>
          </span>
        </h2>
      </div>
      <div>
        <img :src="images.image_1" alt=""/>
      </div>
    </div>
    <div class="ligne">
      <div>
        <h3 v-if="soustitre" class="subtitle">{{soustitre}}</h3>
        <span v-if="bloc == 'departement'">
            <LeMeilleur/>
          </span>
        <div v-if="bloc == 'design' || bloc == 'developpement' || bloc == 'stagealt'">
          <p v-for="(par, index) in texte" :key="index">
            {{par}}
          </p>
        </div>
        <p v-if="texte && bloc != 'design' && bloc != 'developpement' && bloc != 'stagealt'">{{texte}}</p>
        <nuxt-link v-if="lien" :to="`/${link}`" class="action big">En savoir plus</nuxt-link>
        <a v-if="bloc == 'stagealt'" href="https://www.parcoursup.fr/" class="action big" target="_blank" title="Postuler sur ParcourSup (Nouvelle Fenêtre)">Postuler</a>
      </div>
      <div>
        <img :src="images.image_2" alt=""/>
      </div>
    </div>
  </div>
</template>

<script>
import Alternanceini from '~/components/titres/alternanceouini'
import NotreDepartement from '~/components/titres/notredepartement'
import LeMeilleur from '~/components/titres/lemeilleur'
import Design from '~/components/titres/design'
import Developpement from '~/components/titres/developpement'
import Communication from '~/components/titres/communication'
import StageAlt from '~/components/titres/stagealt'

export default {
  props: {
      name: '',
      titre: '',
      soustitre: '',
      texte: '',
      lien: '',
      images: Array,
      image: ''
  },
  components: {
    Alternanceini, NotreDepartement, LeMeilleur, Design, Developpement, Communication, StageAlt
  },
  data() {
    return {
      bloc: '',
      link: ''
    }
  },
  mounted() {
    this.checkBloc();
    this.checkLien();
  },
  methods: {
    checkBloc: function() {
      if(this.name == 'altini') {
        this.bloc = 'altini';
      } else if (this.name == 'departement') {
        this.bloc = 'departement';
      } else if (this.name == 'design') {
        this.bloc = 'design';
      } else if (this.name == 'developpement') {
        this.bloc = 'developpement';
      } else if (this.name == 'communication') {
        this.bloc = 'communication';
      } else if (this.name == 'stagealt') {
        this.bloc = 'stagealt';
      }
    },
    checkLien: function() {
      if(this.lien) {
        console.log(this.lien);
        if(this.lien.includes('formation')) {
          this.link = 'formation';
        } else if(this.lien.includes('departement')) {
          this.link = 'departement';
        }
      }
    }
  }
}
</script>