<template>
  <nav>
    <button id="menuhandle">Ouvre le menu</button>
    <ul id="mainMenu">
        <li><nuxt-link to="/">Accueil</nuxt-link></li>
        <li><nuxt-link to="/formation">Formation</nuxt-link></li>
        <li><nuxt-link to="/departement">Département</nuxt-link></li>
        <li><nuxt-link to="/mobilite">Mobilité Internationale</nuxt-link></li>
        <li><nuxt-link to="/actualites">Actualités</nuxt-link></li>
        <li><nuxt-link to="/contact">Contact</nuxt-link></li>
    </ul>
  </nav>
</template>

<script>
export default {
}
</script>