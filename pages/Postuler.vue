<template>
  <main id="postuler" role="main">
    <div class="gauche">
      <h1>{{titrePostuler}}</h1>
      <a :href="urlPostuler" class="action big dark" target="_blank">S'inscrire via parcoursup</a>
    </div>
    <iframe
      width="956" height="538" :src="urlVideo" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture"
      allowfullscreen
    ></iframe>
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
      urlPostuler: "",
      urlVideo: ""
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
    document.querySelector('body').className = '';
    document.querySelector('body').classList.add('postuler');

    // Get Mentionslégales Data
    axios
      .get("https://palayewordpress.planethoster.world/mmi/wp-json/wp/v2/pages/511?_embed")
      .then(response => {
        this.pageTitle = response.data.title.rendered;

        //headPage
        this.titrePostuler = response.data.acf.titre_postuler;
        this.urlPostuler = response.data.acf.lien_parcoursup;
        this.urlVideo = response.data.acf.video_postuler;
      });
  }
};
</script>
