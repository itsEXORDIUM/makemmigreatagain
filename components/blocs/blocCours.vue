<template>
  <div :class="`wrap ${name}`">
    <div class="bloc_title">
      <h2 class="bloc_titre">{{titre}} <span>{{soustitre}}</span></h2>
      <p>{{texte}}</p>
    </div>
    <ul class="buttons_annees">
      <li><button @click="changeMatiere(1, $event)" class="active">MMI 1</button></li>
      <li><button @click="changeMatiere(2, $event)">MMI 2</button></li>
      <li><button @click="changeMatiere(3, $event)">MMI 3</button></li>
    </ul>
    <div class="lists">
      <h3 class="matiere">Design</h3>
      <p v-for="matiere in active" :key="matiere.title.rendered">
        <span v-if="matiere.acf.domaine.includes('design')">{{matiere.title.rendered}}</span>
      </p>
      <h3 class="matiere">Développement</h3>
      <p v-for="(matiere, index) in active" :key="index">
        <span v-if="matiere.acf.domaine.includes('dev')">{{matiere.title.rendered}}</span>
      </p>
      <h3 class="matiere">Communication</h3>
      <p v-for="matiere in active" :key="matiere.slug">
        <span  v-if="matiere.acf.domaine.includes('com')">{{matiere.title.rendered}}</span>
      </p>
      <h3 class="matiere">Enseignements généraux</h3>
      <p v-for="matiere in active" :key="matiere.link">
        <span v-if="matiere.acf.domaine.includes('general')">{{matiere.title.rendered}}</span>
      </p>
    </div>

  </div>
</template>

<script>
import axios from 'axios'

export default {
  props: {
      name: '',
      titre: '',
      soustitre: '',
      texte: ''
  },
  data() {
    return {
      cours: {},
      mmi1 : [],
      mmi2 : [],
      mmi3 : [],
      active: []
    }
  },
  mounted() {
      // Get Cours
    axios.get('http://51.158.125.115/wp-json/wp/v2/cours?_embed')
      .then(response => {
        this.cours = response.data;

        this.cours.forEach(element => {
          var i = 0;
          for(i-0;i<4;i++) {
            if(element.annee[i] === 12) {
              this.mmi3.push(element);
            }
            if(element.annee[i] === 10) {
              this.mmi2.push(element);
            }
            if(element.annee[i] === 5) {
              this.mmi1.push(element);
            }
          }
        });

        this.active = this.mmi1;
      })
  },
  methods: {
    changeMatiere: function(n, event) {
      document.querySelector('button.active').classList.remove('active');
      if(n === 1) {
        this.active = this.mmi1;
      } else if(n === 2) {
        this.active = this.mmi2;
      } else if(n === 3) {
        this.active = this.mmi3;
      }
      event.target.classList.add('active');
    }
  }
}
</script>