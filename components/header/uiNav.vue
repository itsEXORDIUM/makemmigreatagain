<template>
  <nav>
    <button id="menuhandle" @click="openMenu()">Ouvre le menu</button>
    <div id="mainMenu">
      <div class="wrap">
        <ul class="pages">
          <li @click="closeMenu($event)" data-lien="accueil"><nuxt-link to="/">Accueil</nuxt-link></li>
          <li @click="closeMenu($event)" data-lien="formation"><nuxt-link to="/formation">Formation</nuxt-link></li>
          <li @click="closeMenu($event)" data-lien="departement"><nuxt-link to="/departement">Département</nuxt-link></li>
          <li @click="closeMenu($event)" data-lien="mobilite"><nuxt-link to="/mobilite">Mobilité Internationale</nuxt-link></li>
          <li @click="closeMenu($event)" data-lien="actu"><nuxt-link to="/actualites">Actualités</nuxt-link></li>
          <li @click="closeMenu($event)" data-lien="contact"><nuxt-link to="/contact">Contact</nuxt-link></li>
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
    },
    closeMenu: function(event) {
      document.getElementById('mainMenu').classList.remove('open');
      document.getElementById('menuhandle').classList.remove('toCross');

      this.main = event.target.closest('li').dataset.lien;
      console.log(event.target.closest('li').dataset.lien);
      this.checkPage();
    },
    checkPage: function() {
      if(this.main === 'mobilite' || this.main === 'departement' || this.main === 'error') {
        document.querySelector('body').style.backgroundColor = '#106466';
      } else if(this.main === 'mentionsleg') {
        document.querySelector('body').style.backgroundColor = '#D8B08C';
      } else if (this.main === 'actu') {
        document.querySelector('body').style.backgroundColor = '#FFCB9B';
      } else {
        document.querySelector('body').style.backgroundColor = '#2C3532';
      }
    }
  }
}
</script>