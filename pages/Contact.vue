<template>
  <main id="contact" role="main">
    <HeadPage name="venezvoir" :quandmeme="true" :titre="titrevenez" :texte="textevenez"/>
    <BlocForums name="bloc_forums" :titre="titreforum" :image="imageforum" :texte="texteforum" :titredeux="titrejpo" :imagedeux="imagejpo" :textedeux="textejpo"/>
    <BlocHome name="espacepro" :titre="titreespacepro" :image='imageespacepro' :texte="texteespacepro" :lien="lienespacepro"/>
    <BlocHome name="adoptalt" :titre="titrealternant" :image='imagealternant' :texte="textealternant" :lien="lienalt"/>
    <BlocHome name="unprojet" :titre="titreprojet" :image='imageprojet' :texte="texteprojet" :lien="lienprojet"/>
    <div class="bloc_home wrap contacteznous">
      <h2 class="bloc_titre">
        <span class="show-for-sr">{{titrecoordonnees}}</span>
        <ContactezNous/>
      </h2>
      <div>
        <p>{{intitule}}</p>
        <p>{{rue}}</p>
        <p>{{ville}}</p>
        <p>Tél. {{telephone}}</p>
        <p>Mail : {{mail}}</p>
      </div>
    </div>
  </main>
</template>

<script>
import axios from 'axios'
import HeadPage from '~/components/head_pages/headpage'
import BlocForums from '~/components/blocs/blocforums'
import BlocHome from '~/components/blocs/blocHome'
import ContactezNous from '~/components/titres/contacteznous'

export default {
  components: {
    HeadPage, BlocForums, BlocHome, ContactezNous
  },
  data() {
    return {
      pageTitle: '',
      titrevenez: '',
      textevenez: '',
      titreforum: '',
      imageforum: '',
      texteforum: '',
      titrejpo: '',
      imagejpo: '',
      textejpo: '',
      titreespacepro: '',
      imageespacepro: '',
      texteespacepro: '',
      lienespacepro: '',
      titrealternant: '',
      imagealternant: '',
      textealternant: '',
      lienalt: '',
      titreprojet: '',
      imageprojet: '',
      texteprojet: '',
      lienprojet: '',
      titrecoordonnees: '',
      intitule: '',
      rue: '',
      ville: '',
      telephone: '',
      mail: ''
    }
  },
  head () {
    return {
      title: this.pageTitle,
      meta: [
        // hid is used as unique identifier. Do not use `vmid` for it as it will not work
        { hid: 'description', name: 'description', content: 'My custom description' }
      ]
    }
  },
  mounted() {
    document.querySelector('body').className = '';
    document.querySelector('body').classList.add('contact');

    // Get Contact Data
    axios.get('https://palayewordpress.planethoster.world/mmi/wp-json/wp/v2/pages/21?_embed')
      .then(response => {
        this.pageTitle = response.data.title.rendered;
        
        // Head page
        this.titrevenez = response.data.acf.titre_venez;
        this.textevenez = response.data.acf.texte_venez;

        // Forums etudiants jpo
        this.titreforum = response.data.acf.titre_forum;
        this.imageforum = response.data.acf.image_forum;
        this.texteforum = response.data.acf.texte_forum;
        this.titrejpo = response.data.acf.titre_jpo;
        this.imagejpo = response.data.acf.image_jpo;
        this.textejpo = response.data.acf.texte_jpo;

        // ESPACE PRO
        this.titreespacepro = response.data.acf.titre_espace_pro;
        this.imageespacepro = response.data.acf.image_espace_pro;
        this.texteespacepro = response.data.acf.texte_espace_pro;
        this.lienespacepro = response.data.acf.lien_espace_pro;

        // ADPOTER UN ALTERNANT
        this.titrealternant = response.data.acf.titre_alternant;
        this.imagealternant = response.data.acf.image_alternant;
        this.textealternant = response.data.acf.texte_alternant;
        this.lienalt = response.data.acf.lien_alt;

        // UN PROJET
        this.titreprojet = response.data.acf.titre_projet;
        this.imageprojet = response.data.acf.image_projet;
        this.texteprojet = response.data.acf.texte_projet;
        this.lienprojet = response.data.acf.lien_projet;

        // CONTACTEZ NOUS
        this.titrecoordonnees = response.data.acf.titre_coordonnees;
        this.intitule = response.data.acf.intitule;
        this.rue = response.data.acf.rue;
        this.ville = response.data.acf.ville;
        this.telephone = response.data.acf.telephone;
        this.mail = response.data.acf.mail;
      })
  }
}
</script>
