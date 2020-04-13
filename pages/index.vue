<template>
  <div id="accueil">
    <Accueil :headPage="headPage"/>
    <BlocHome :titre="titrepolyvalents" :texte="textepolyvalents" :lien="lienpolyvalents" :images="imagespolyvalents"/>
    <BlocHome :titre="titrealtinit" :texte="textealtini" :lien="lienaltinit" :images="imagesaltinit"/>
  </div>
</template>

<script>
import axios from 'axios'
import Accueil from '~/components/head_pages/accueil'
import BlocHome from '~/components/blocs/blocHome'

export default {
  components: {
    Accueil, BlocHome
  },
  data() {
    return {
      homeData: [],
      headPage: '',
      titrepolyvalents : '',
      textepolyvalents : '',
      lienpolyvalents : '',
      imagespolyvalents: [],
      titrealtinit: '',
      textealtini: '',
      lienaltinit: '',
      imagesaltinit: []
    }
  },
  mounted() {
      // Get Accueil Data
    axios.get('http://51.158.125.115/wp-json/wp/v2/pages/8?_embed')
      .then(response => {
          this.homeData = response.data;
          this.headPage = response.data.content.rendered;

          // Etudiants polyvalents
          this.titrepolyvalents = response.data.acf.titre_polyvalents;
          this.textepolyvalents = response.data.acf.texte_polyvalents;
          this.lienpolyvalents = response.data.acf.lien_etudiants_polyvalents;
          this.imagespolyvalents = response.data.acf.images_polyvalents;

          // Alternance ou initial
          this.titrealtinit = response.data.acf.titre_alt_init;
          this.textealtini = response.data.acf.texte_alt_ini;
          this.lienaltinit = response.Data.acf.lien_alt_init;
          this.imagesaltinit = response.data.acf.images_alt_init;
      })
  }
}
</script>
