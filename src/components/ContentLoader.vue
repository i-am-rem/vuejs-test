<template>
  <content-loader
    :width="400"
    :height="150"
    :speed="2"
    primaryColor="#f3f3f3"
    secondaryColor="#ecebeb"
  >
    <circle cx="10" cy="20" r="8" /> 
    <rect x="25" y="14" rx="5" ry="5" width="300" height="10" /> 
    <circle cx="10" cy="50" r="8" /> 
    <rect x="27" y="44" rx="5" ry="5" width="300" height="10" /> 
    <circle cx="10" cy="80" r="8" /> 
    <rect x="25" y="75" rx="5" ry="5" width="300" height="10" /> 
    <circle cx="10" cy="110" r="8" /> 
    <rect x="25" y="105" rx="5" ry="5" width="300" height="10" /> 
    <rect x="27" y="132" rx="5" ry="5" width="300" height="10" /> 
    <circle cx="9" cy="138" r="8" />
  </content-loader>
</template>
<script>
/**
 * imports content loader plugin
 */
import { ContentLoader } from 'vue-content-loader'

export default {
  components: {
    ContentLoader
  }
}
</script>