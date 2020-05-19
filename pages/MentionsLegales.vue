<template>
  <main id="mentionsleg">
    <div class="head_page">
      <h1>
        <span class="show-for-sr">{{titreMentionsleg}}</span>
        <Mentionsleg />
      </h1>
      <button class="ancre">
        <span class="show-for-sr">Découvrir MMI Montbéliard</span>
      </button>
    </div>
    <BlocDroitsAuteurs :name="namedroitsauteurs" :titre="titredroitsauteurs" :titreloi="titreloi" :texteloi="texteloi" :titredroitsauteurs="titredroitsauteurs" :textedroitsauteurs="textedroitsauteurs"/>
  </main>
</template>

<script>
import axios from "axios";
import Mentionsleg from "~/components/titres/mentionsleg";
import BlocDroitsAuteurs from "~/components/blocs/blocDroitsAuteurs";

export default {
  components: {
    Mentionsleg, BlocDroitsAuteurs
  },
  data() {
    return {
      titreMentionsleg: '',
      namedroitsauteurs: 'blocdroitsauteurs',
      titredroitsauteurs: '',
      titreloi: '',
      texteloi: '',
      titredroitsauteurs: '',
      textedroitsauteurs: ''
    };
  },
  mounted() {
    // Get Mentionslégales Data
    axios
      .get("http://51.158.125.115/wp-json/wp/v2/pages/12?_embed")
      .then(response => {
        // Headpage
        this.titreMentionsleg = response.data.acf.titre_mentions_legales;

        // Droits d'auteurs
        this.titredroitsauteurs = response.data.acf.titre_droits_auteurs;
        this.titreloi = response.data.acf.groupe_1_droits_auteurs.titre;
        this.texteloi = response.data.acf.groupe_1_droits_auteurs.texte;
        this.titredroitsauteurs = response.data.acf.groupe_2_droits_auteurs.titre;
        this.textedroitsauteurs = response.data.acf.groupe_2_droits_auteurs.texte;
      });
  }
};
</script>
