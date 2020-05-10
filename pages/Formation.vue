<template>
  <div id="formation">
    <Formation :headPage="headPage"/>
    <BlocHome :name="nameformation" :titre="titreformation" :texte="texteformation" :image="imageformation"/>
    <BlocHomeV2 :name="namedesign" :titre="titredesign" :texte="textedesign" :images="imagesdesign"/>
  </div>
</template>

<script>
import axios from 'axios'
import Formation from '~/components/head_pages/formation'
import BlocHome from '~/components/blocs/blocHome'
import BlocHomeV2 from '~/components/blocs/blocHomeV2'

export default {
  components: {
    Formation, BlocHome, BlocHomeV2
  },
  data() {
    return {
      FormationData: [],
      headPage: '',
      nameformation: 'formation',
      titreformation: '',
      texteformation: '',
      imageformation: [],
      namedesign : 'design',
      titredesign: '',
      textedesign: [],
      imagesdesign: []
    }
  },
  mounted() {
      // Get Accueil Data
    axios.get('http://51.158.125.115/wp-json/wp/v2/pages/10?_embed')
      .then(response => {
          this.FormationData = response.data;
          this.headPage = response.data.content.rendered;

          // Formation
          this.titreformation = response.data.acf.titre_formation;
          this.texteformation = response.data.acf.texte_formation;
          this.lienpays = response.data.acf.lien_voir_du_pays;
          this.imageformation = response.data.acf.image_formation;

          // Le Design
          this.titredesign = response.data.acf.titre_design;
          this.textedesign = response.data.acf.textes_design;
          this.imagesdesign = response.data.acf.images_design;
      })
  }
}
</script>
