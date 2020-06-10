<template>
  <div :class="`wrap ${name}`">
    <div class="bloc_title wrap">
      <h2 class="bloc_titre">
        <span class="show-for-sr">{{titre}}</span>
        <DroitsAuteurs />
      </h2>
    </div>
    <div class="textedroitauteur">
      <div class="blocgauche">
        <h3>{{titreloi}}</h3>
        <p>{{texteloi}}</p>
      </div>
      <div class="blocdroit">
        <h3>{{titredroitsauteurs}}</h3>
        <p>{{textedroitsauteurs}}</p>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
import DroitsAuteurs from "~/components/titres/droitsauteurs";

export default {
  props: {
    name: "",
    titre: "",
    titreloi: "",
    texteloi: "",
    titredroitsauteurs: "",
    textedroitsauteurs: ""
  },
  components: {
    DroitsAuteurs
  }
};
</script>