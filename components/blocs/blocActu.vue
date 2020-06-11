<template>
  <div :class="`wrap ${name}`">
      <ul class="buttons_reseaux">
        <li><button role="tab" aria-selected="true" @click="changeReseau1(1, $event)" id="tous" class="active">Tous</button></li>
        <li><button role="tab" aria-selected="true" @click="changeReseau2(1, $event)" id="twitter" class="active">twitter</button></li>
        <li><button role="tab" aria-selected="true" @click="changeReseau3(2, $event)" id="facebook">facebook</button></li>
        <li><button role="tab" aria-selected="true" @click="changeReseau4(3, $event)" id="instagram">instagram</button></li>
    </ul>
  </div>
</template>

<script>
import axios from "axios";

export default {
  props: {
    name: ""
  }
};
</script>