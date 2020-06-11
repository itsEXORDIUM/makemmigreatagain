<template>
  <main id="postuler" role="main">
    <h1>{{titrePostuler}}</h1>
    <a :href="urlPostler" class="action big dark">Voir le profil des étudiants</a>
    <iframe width="956" height="538" :src="urlVideo" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
  </main>
</template>

<script>
import axios from "axios";

export default {
  components: {},
  data() {
    return {
      pageTitle: "",
      titrePostuler: "",
      urlPostler: "",
      urlVideo: "",
    };
  },
  head() {
    return {
      title: this.pageTitle,
      meta: [
        // hid is used as unique identifier. Do not use `vmid` for it as it will not work
        {
          hid: "description",
          name: "description",
          content: "My custom description"
        }
      ]
    };
  },
  mounted() {
    // Get Mentionslégales Data
    axios
      .get("http://51.158.125.115/wp-json/wp/v2/pages/511?_embed")
      .then(response => {
        this.pageTitle = response.data.title.rendered;

        //headPage
        this.titrePostuler = response.data.acf.titre_postuler;
        this.urlPostler = response.data.acf.lien_parcoursup;
        this.urlVideo = response.data.acf.video_postuler;
      });
  }
};
</script>
