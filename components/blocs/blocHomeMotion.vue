<template>
  <div :class="`bloc_home v2 wrap ${name}`">
    <div class="ligne">
      <div>
        <h2 class="bloc_titre">
          <span class="show-for-sr">{{titre}}</span>
            <MotionDesign/>
        </h2>
      </div>
      <div>
        <video width="100%" height="768" controls>
          <source :src="video_1" type="video/mp4">
        Your browser does not support the video tag.
        </video>
      </div>
    </div>
    <div class="ligne">
      <div>
        <p>{{texte_1}}</p>
        <h3 class="subtitle">{{soustitre}}</h3>
        <p>{{texte_2}}</p>
      </div>
      <div>
        <video width="100%" height="879" controls>
          <source :src="video_2" type="video/mp4">
        Your browser does not support the video tag.
        </video>
      </div>
    </div>
  </div>
</template>

<script>
import MotionDesign from '~/components/titres/motiondesign'

export default {
  props: {
      name: '',
      titre: '',
      soustitre: '',
      texte_1: '',
      texte_2: '',
      video_1: '',
      video_2: ''
  },
  components: {
    MotionDesign
  },
  data() {
    return {
    }
  }
}
</script>