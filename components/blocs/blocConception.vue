<template>
  <div :class="`wrap ${name}`">
    <div class="bloc_title wrap">
      <h2 class="bloc_titre">
        <span class="show-for-sr">{{titre}}</span>
        <Conception />
      </h2>
    </div>
    <div class="membres">
      <div class="membre" v-for="(mb, index) in membres" :key="index">
        <img :src="mb.image" alt />
        <h3>{{mb.nom}}</h3>
        <p>{{mb.role}}</p>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
import Conception from "~/components/titres/conceptionetrealisation";

export default {
  props: {
    name: "",
    titre: ""
  },
  components: {
    Conception
  },
  data() {
    return {
      membres: []
    };
  },
  mounted() {
    axios
      .get("https://palayewordpress.planethoster.world/mmi/wp-json/wp/v2/pages/12?_embed")
      .then(response => {
        this.membres = response.data.acf.groupe_conception;
      });
  }
};
</script>