<template>
  <main id="actu" role="main">
    <div class="head_page">
      <h1>
        <span class="show-for-sr">{{titreActu}}</span>
        <Actu />
      </h1>
      <button class="ancre">
        <span class="show-for-sr">Découvrir les actualités</span>
      </button>
    </div>
    <BlocActu :name="nameActu"/>
  </main>
</template>

<script>
import axios from "axios";
import Actu from "~/components/titres/quoideneuf";
import BlocActu from "~/components/blocs/blocActu";

export default {
  components: {
    Actu, BlocActu
  },
  data() {
    return {
      pageTitle: '',
      titreActu: '',
      nameActu: 'actualite',
    };
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
    document.querySelector('body').classList.add('actu');

    // Get Mentionslégales Data
    axios
      .get('https://palayewordpress.planethoster.world/mmi/wp-json/wp/v2/pages/19?_embed')
      .then(response => {
        this.pageTitle = response.data.title.rendered;

        // Headpage
        this.titreActu = response.data.acf.titre_actualite;

      });
  }
};
</script>
