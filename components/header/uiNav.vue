<template>
  <nav role="navigation">
    <button id="menuhandle" tabindex="0" aria-label="Ouvre ou ferme le menu" aria-pressed="false" role="button" @click="openMenu()">Ouvre/Ferme le menu</button>
    <div id="mainMenu">
      <div class="wrap">
        <ul class="pages">
          <li @click="closeMenu($event)" data-lien="accueil"><nuxt-link to="/" title="Aller à l'accueil">Accueil</nuxt-link></li>
          <li @click="closeMenu($event)" data-lien="formation"><nuxt-link to="/formation" title="Aller à la page formation">Formation</nuxt-link></li>
          <li @click="closeMenu($event)" data-lien="departement"><nuxt-link to="/departement" title="Aller à la page département">Département</nuxt-link></li>
          <li @click="closeMenu($event)" data-lien="mobilite"><nuxt-link to="/mobilite" title="Aller à la page mobilité internationale">Mobilité Internationale</nuxt-link></li>
          <li @click="closeMenu($event)" data-lien="actu"><nuxt-link to="/actualites" title="Aller à la page atualités">Actualités</nuxt-link></li>
          <li @click="closeMenu($event)" data-lien="contact"><nuxt-link to="/contact" title="Aller à la page contact">Contact</nuxt-link></li>
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
  data() {
    return {
      main:''
    }
  },
  mounted() {
    this.main = document.querySelector('main').id;
    this.checkPage();
  },
  methods: {
    openMenu: function() {
      document.getElementById('mainMenu').classList.toggle('open');
      document.getElementById('menuhandle').classList.toggle('toCross');
      document.getElementById('menuhandle').setAttribute('aria-pressed', true);
      var body = document.querySelector('body');
      
      if(body.classList.contains('overlay')) {
        body.classList.remove('overlay');
      } else {
        body.classList.add('overlay');
      }
    },
    closeMenu: function(event) {
      document.getElementById('mainMenu').classList.remove('open');
      document.getElementById('menuhandle').classList.remove('toCross');
      document.getElementById('menuhandle').setAttribute('aria-pressed', false);
      document.querySelector('body').classList.remove('overlay');

      this.main = event.target.closest('li').dataset.lien;
      console.log(event.target.closest('li').dataset.lien);
      this.checkPage();
    },
    checkPage: function() {
      document.querySelector('body').className = '';
      document.querySelector('body').classList.add(this.main);
    }
  }
}
</script>