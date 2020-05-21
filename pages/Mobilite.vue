<template>
   <main id="mobilite">
     <HeadPage :titre="titremobilite" :image="imagemobilite" :texte="textemobilite"/>
     <BlocHome :name="namestage" :titre="titrestage" :texte="textestage" :image="imagestage"/>
     <BlocHomeV2 :name="namecanada" :titre="titrecanada" :texte="textecanada" :images="imagescanada"/>
     <BlocHomeV2 name="barcelone" :titre="titrebarcelone" :texte="textebarcelone" :images="imagesbarcelone" :video="videobarcelone"/>
     <div class="wrap rejoignez">
       <h2 class="bloc_titre">
          <span class="show-for-sr">{{titrerejoindre}}</span>
          <Rejoignez/>
        </h2>
        <nuxt-link to="/postuler" class="action big dark">Postuler</nuxt-link>
     </div>
   </main>
</template>

<script>
import axios from 'axios'
import HeadPage from '~/components/head_pages/mobilite'
import BlocHome from '~/components/blocs/blocHome'
import BlocHomeV2 from '~/components/blocs/blocHomeV2'
import Rejoignez from '~/components/titres/rejoignez'

export default {
  components: {
    HeadPage, BlocHome, BlocHomeV2, Rejoignez
  },
  data() {
    return {
      titremobilite: '',
      imagemobilite: '',
      textemobilite: '',
      namestage: 'stageetranger',
      titrestage: '',
      textestage: '',
      imagestage: '',
      namecanada: 'canada',
      titrecanada: '',
      imagescanada: [],
      textecanada: '',
      titrebarcelone: '',
      imagesbarcelone: [],
      textebarcelone: '',
      videobarcelone: [],
      titrerejoindre: ''
    }
  },
  mounted() {
    // Get Mobilite Data
    axios.get('http://51.158.125.115/wp-json/wp/v2/pages/17?_embed')
      .then(response => {
          // Headpage
          this.titremobilite = response.data.acf.titre_mobilite;
          this.imagemobilite = response.data.acf.image_mobilite.url;
          this.textemobilite = response.data.acf.texte_mobilite;

          // Stage Etranger
          this.titrestage = response.data.acf.titre_stage_etranger;
          this.textestage = response.data.acf.texte_stage_etranger;
          this.imagestage = response.data.acf.image_stage_etranger.url;

          // Semestre Canada
          this.titrecanada = response.data.acf.titre_canada;
          this.imagescanada = response.data.acf.images_canada;
          this.textecanada = response.data.acf.texte_canada;

          // Semaine Barcelone
          this.titrebarcelone = response.data.acf.titre_barcelone;
          this.imagesbarcelone = response.data.acf.images_barcelone;
          this.textebarcelone = response.data.acf.texte_barcelone;
          this.videobarcelone = response.data.acf.video_barcelone;

          // Rejoignez nous
          this.titrerejoindre = response.data.acf.titre_rejoindre;
      })
  }
}
</script>
