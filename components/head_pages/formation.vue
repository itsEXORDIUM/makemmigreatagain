<template>
  <div class="head_page">
    <div class="left">
      <div class="content wrap">
        <div v-html="headPage"></div>
      </div>
    </div>
    <div class="right">
      <img src="~/static/imgs/studentComputer.png" alt=""/>
    </div>
    <button class="ancre"><span class="show-for-sr">Découvrir la formation MMI Montbéliard</span></button>
  </div>
</template>

<script>
export default {
  props: {
    headPage: ''
  }
}
</script>