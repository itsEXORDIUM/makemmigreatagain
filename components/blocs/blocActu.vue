<template>
  <div :class="`wrap ${name}`">
    <ul class="buttons_reseaux">
      <li><button role="tab" aria-selected="true" @click="changeReseau(0, $event)" id="tous" class="active">Tous</button></li>
      <li><button role="tab" aria-selected="true" @click="changeReseau(1, $event)" id="twitter">twitter</button></li>
      <li><button role="tab" aria-selected="true" @click="changeReseau(2, $event)" id="facebook">facebook</button></li>
      <li><button role="tab" aria-selected="true" @click="changeReseau(3, $event)" id="instagram">instagram</button></li>
    </ul>
    <div class="lists">
      <div v-for="actu in active" :key="actu.title.rendered" :class="actu.acf.reseau_actu" class="post">
        <img v-if="actu.acf.image_actu" :src="actu.acf.image_actu" />
        <div v-if="actu.acf.reseau_actu==='facebook'" class="filtre"></div>
        <p v-if="actu.acf.texte_actu">{{actu.acf.texte_actu}}</p>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  props: {
    name: ""
  },
  data() {
    return {
      actualites: {},
      facebook: [],
      instagram: [],
      twitter: [],
      active: []
    };
  },
  mounted() {
    axios
      .get(
        "https://palayewordpress.planethoster.world/mmi/wp-json/wp/v2/actus?_embed"
      )
      .then(response => {
        this.actualites = response.data;

        this.actualites.forEach(element => {
          if (element.acf.reseau_actu == "facebook") {
            this.facebook.push(element);
          }
          if (element.acf.reseau_actu == "instagram") {
            this.instagram.push(element);
          }
          if (element.acf.reseau_actu == "twitter") {
            this.twitter.push(element);
          }
        });

        this.active = this.actualites;
      });
  },
  methods: {
    changeReseau: function(n, event) {
      var active = document.querySelector("button.active");
      active.classList.remove("active");
      active.setAttribute("aria-selected", false);
      if (n === 0) {
        this.active = this.actualites;
        document.getElementById("tous").setAttribute("aria-selected", true);
      } else if (n === 1) {
        this.active = this.twitter;
        document.getElementById("twitter").setAttribute("aria-selected", true);
      } else if (n === 2) {
        this.active = this.facebook;
        document.getElementById("facebook").setAttribute("aria-selected", true);
      } else if (n === 3) {
        this.active = this.instagram;
        document
          .getElementById("instagram")
          .setAttribute("aria-selected", true);
      }
      event.target.classList.add("active");
    }
  }
};
</script>