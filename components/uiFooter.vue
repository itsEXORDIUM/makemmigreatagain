<template>
  <footer>
      <div id="logoFooter">
        <nuxt-link to="/">MMI Montbéliard</nuxt-link>
      </div>
      <ul id="links">
        <li><a class="iut" href="#" target="_blank" title="Ouvrir le site de l'IUT (Nouvelle Fenêtre)">IUT Belfort Montbéliard</a></li>
        <li><a class="linkedin reseaux" href="#" target="_blank" title="Suivre MMI Montbéliard sur LinkedIn (Nouvelle Fenêtre)">LinkedIn</a></li>
        <li><a class="facebook reseaux" href="#" target="_blank" title="Suivre MMI Montbéliard sur Facebook (Nouvelle Fenêtre)">Facebook</a></li>
        <li><a class="insta reseaux" href="#" target="_blank" title="Suivre MMI Montbéliard sur Instagram (Nouvelle Fenêtre)">Instagram</a></li>
        <li><a class="twitter reseaux" href="#" target="_blank" title="Suivre MMI Montbéliard sur Twitter (Nouvelle Fenêtre)">Twitter</a></li>
        <li><a class="universitefc" href="#" target="_blank" title="Ouvrir le site de l'Université (Nouvelle Fenêtre)">Université de France-Comté</a></li>
      </ul>
      <div id="contact">
        <p class="intitule">Département métiers du multimédia et de l'internet de Montbéliard</p>
        <p class="adresse"><span>4, place Tharradin - 25 200 Montbéliard</span> <span>- Tél. <a href="0381994734">03 81 99 47 34</a></span></p>
        <p data-lien="mentionsleg" @click="setPage()"><nuxt-link to="/mentionslegales">Mentions légales</nuxt-link></p>
      </div>
      <a id="backToTop" href="#top"><span class="show-for-sr">Retourner en </span>Haut de page</a>
  </footer>
</template>

<script>
export default {
  mounted() {
  },
  methods: {
    backToTop: function() {
      this.$el.stop().animate({
        scrollTop: 0
      }, 'slow', 'swing');
    },
    setPage: function() {
      document.querySelector('body').style.backgroundColor = '#D8B08C';
    }
  }
}
</script>