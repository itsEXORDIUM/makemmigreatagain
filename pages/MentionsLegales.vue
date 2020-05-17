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
  </main>
</template>

<script>
import axios from "axios";
import Mentionsleg from "~/components/titres/mentionsleg";

export default {
  components: {
    Mentionsleg
  },
  data(){
    return{
      titreMentionsleg: 'Mentions légales'
    }
  }
};
</script>
