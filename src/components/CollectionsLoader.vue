<template>
    <content-loader
        :width="400"
        :height="460"
        :speed="2"
        primaryColor="#f3f3f3"
        secondaryColor="#ecebeb"
        >
        <rect x="-13" y="-1" rx="2" ry="2" width="400" height="350" /> 
        <rect x="205" y="454" rx="0" ry="0" width="0" height="2" /> 
        <rect x="141" y="457" rx="0" ry="0" width="0" height="1" /> 
        <rect x="0" y="362" rx="0" ry="0" width="373" height="10" /> 
        <rect x="2" y="382" rx="0" ry="0" width="300" height="10" /> 
        <rect x="3" y="405" rx="0" ry="0" width="251" height="10" />
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