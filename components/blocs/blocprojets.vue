<template>
  <div class="bloc_projets">
    <div class="bloc_title wrap">
      <h2 class="bloc_titre"><span class="show-for-sr">{{titre}}</span>
          <Projets/>
      </h2>
    </div>
    <div class="galerie">
      <div class="projet" v-for="(projet, index) in projets" :key="index">
        <div class="content">
          <h3 class="titre_projet">{{projet.title.rendered}}</h3>
          <p class="nom">{{projet.acf.auteur}}</p>
          <p class="promo">{{projet.acf.promo}}</p>
        </div>
        <a :href="projet.acf.lien" :title="`Voir le projet ${projet.title.rendered} (Nouvelle fenêtre)`" target="_blank"><span class="show-for-sr">Voir le projet</span></a>
        <img :src="projet.acf.image" alt=""/>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
import Projets from '~/components/titres/Projets'

export default {
  props: {
      titre: ''
  },
  components: {
    Projets
  },
  data() {
    return {
      projets: []
    }
  },
  mounted() {
     // Get Temoignages
    axios.get('http://51.158.125.115/wp-json/wp/v2/projets')
      .then(response => {
          this.projets = response.data;
      })
  }
}
</script>