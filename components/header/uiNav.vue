<template>
  <nav>
    <button id="menuhandle" @click="openMenu()">Ouvre le menu</button>
    <div id="mainMenu">
      <div class="wrap">
        <ul class="pages">
          <li><nuxt-link to="/">Accueil</nuxt-link></li>
          <li><nuxt-link to="/formation">Formation</nuxt-link></li>
          <li><nuxt-link to="/departement">Département</nuxt-link></li>
          <li><nuxt-link to="/mobilite">Mobilité Internationale</nuxt-link></li>
          <li><nuxt-link to="/actualites">Actualités</nuxt-link></li>
          <li><nuxt-link to="/contact">Contact</nuxt-link></li>
        </ul>

        <ul class="reseaux">
          <li><a class="linkedin" href="http://www.linkedin.com/company/src-media" target="_blank" title="Suivre MMI Montbéliard sur LinkedIn (Nouvelle Fenêtre)">LinkedIn</a></li>
          <li><a class="facebook" href="http://www.facebook.com/mmimontbeliard" target="_blank" title="Suivre MMI Montbéliard sur Facebook (Nouvelle Fenêtre)">Facebook</a></li>
          <li><a class="insta" href="http://instagram.com/mmi_montbeliard" target="_blank" title="Suivre MMI Montbéliard sur Instagram (Nouvelle Fenêtre)">Instagram</a></li>
          <li><a class="twitter" href="http://twitter.com/MMImontbeliard" target="_blank" title="Suivre MMI Montbéliard sur Twitter (Nouvelle Fenêtre)">Twitter</a></li>
        </ul>
      </div>
    </div>
  </nav>
</template>

<script>
export default {
  methods: {
    openMenu: function() {
      document.getElementById('mainMenu').classList.toggle('open');
      document.getElementById('menuhandle').classList.toggle('toCross');
    }
  }
}
</script>