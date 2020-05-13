<template>
  <main id="formation">
    <Formation :headPage="headPage"/>
    <BlocHome :name="nameformation" :titre="titreformation" :texte="texteformation" :image="imageformation"/>
    <BlocHomeV2 :name="namedesign" :titre="titredesign" :texte="textedesign" :images="imagesdesign"/>
    <BlocHomeV2 :name="namedev" :titre="titredev" :texte="textedev" :images="imagesdev"/>
    <BlocHomeV2 :name="namecom" :titre="titrecom" :texte="textecom" :images="imagescom"/>
    <BlocHomeMotion :name="namemotion" :titre="titremotion" :soustitre="soustitremotion" :texte_1="texte1motion" :texte_2="texte2motion" :video_1="vid1motion" :video_2="vid2motion"/>
    <BlocCours :name="namecours" :titre="titrecours" :soustitre="soustitrecours" :texte="textecours"/>
    <BlocHomeV2 :name="namestagealternant" :titre="titrestagealternant" :texte="textesstagealternant" :images="imagesstagealternant"/>
    <BlocBoss :name="nameboss" :titre="titreboss" :infosun="infosbossun" :infosdeux="infosbossdeux" :infostrois="infosbosstrois" :texte="texteboss"/>
    <BlocProjets :titre="titreprojets"/>
  </main>
</template>

<script>
import axios from 'axios'
import Formation from '~/components/head_pages/formation'
import BlocHome from '~/components/blocs/blocHome'
import BlocHomeV2 from '~/components/blocs/blocHomeV2'
import BlocHomeMotion from '~/components/blocs/blocHomeMotion'
import BlocCours from '~/components/blocs/blocCours'
import BlocBoss from '~/components/blocs/blocboss'
import BlocProjets from '~/components/blocs/blocprojets'

export default {
  components: {
    Formation, BlocHome, BlocHomeV2, BlocHomeMotion, BlocCours, BlocBoss, BlocProjets
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
      imagesdesign: [],
      namedev : 'developpement',
      titredev: '',
      textedev: [],
      imagesdev: [],
      namecom : 'communication',
      titrecom: '',
      textecom: [],
      imagescom: [],
      namemotion : 'motion',
      titremotion: '',
      soustitremotion: '',
      texte1motion: '',
      texte2motion: '',
      vid1motion: '',
      vid2motion: '',
      namestagealternant : 'stagealt',
      titrestagealternant: '',
      textesstagealternant: [],
      imagesstagealternant: [],
      namecours:'bloc_lescours',
      titrecours: '',
      soustitrecours: '',
      textecours: '',
      nameboss: 'blocboss',
      titreboss: '',
      infosbossun: [],
      infosbossdeux: [],
      infosbosstrois: [],
      texteboss: '',
      titreprojets: ''
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

          // Le Developpement
          this.titredev = response.data.acf.titre_developpement;
          this.textedev = response.data.acf.textes_developpement;
          this.imagesdev = response.data.acf.images_developpement;

          // La Communication
          this.titrecom = response.data.acf.titre_communication;
          this.textecom = response.data.acf.texte_communication;
          this.imagescom = response.data.acf.images_communication;

          // Le Motion
          this.titremotion = response.data.acf.titre_motion;
          this.soustitremotion = response.data.acf.sous_titre_motion;
          this.texte1motion = response.data.acf.texte_1_motion;
          this.texte2motion = response.data.acf.texte_2_motion;
          this.vid1motion = response.data.acf.videos_motion.video_1;
          this.vid2motion = response.data.acf.videos_motion.video_2;

          // Stages Alternance
          this.titrestagealternant = response.data.acf.titre_stage_alternant;
          this.imagesstagealternant = response.data.acf.images_stage_alternant;
          this.textesstagealternant = response.data.acf.textes_stage_alternant;

          // Les cours
          this.titrecours = response.data.acf.titre_cours_bref;
          this.soustitrecours = response.data.acf.soustitre_cours_bref;
          this.textecours = response.data.acf.texte_cours_bref;

          // Le Boss
          this.titreboss = response.data.acf.titre_boss;
          this.infosbossun = response.data.acf.infos_boss.texte_1;
          this.infosbossdeux = response.data.acf.infos_boss.texte_2;
          this.infosbosstrois = response.data.acf.infos_boss.texte_3;
          this.texteboss = response.data.acf.texte_boss;

          // Les projets
          this.titreprojets = response.data.acf.titre_projets;
      })
  }
}
</script>
