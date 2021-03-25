<template>
  <div class="home">
   <div class="container">
     <div class="row">
        <div v-if="!isloading" class="container-fluid py-5 col-lg-4">
          <h1 class="display-5 fw-bold">{{ title }}</h1>
          <p class="col-md-8 fs-4">{{ description }}</p>
        </div>
        <!-- Content loader -->
        <div v-else class="container-fluid py-5 col-lg-4">
            <content-loader-component></content-loader-component>
        </div>
        <!-- end of content loader -->
        <div class="container-fluid py-8 col-lg-4">
          <counter :numbers="randomNumbers"></counter>
        </div>
      </div>
    </div>
</div>
</template>

<script>
import Counter from '@/components/Blocks.vue'
import ContentLoaderComponent from '@/components/ContentLoader.vue'
import axios from 'axios'


export default {
  name: 'Home',
  components: {
    Counter,
    ContentLoaderComponent
  },
  data() {
    return {
      randomNumbers:[100, 0, 0,1],
      title:"",
      description: "",
      isloading: true
    }
  },
  created() {
    this.getContent()
  },
  methods:{
    /**
     * sets the title & the description
     * */ 
    async getContent() {
      const content =  axios.get('/static.json')
      await content.then(response => {
        console.log(response)
        let delay = (response.data) ?  
          setTimeout(() => {
            this.isloading = false
            this.title = response.data.title
            this.description = response.data.description
          }, 3000) 
          : this.isloading = true ;
        delay
      }).catch(error => {
        console.log(error)
        this.isloading = false
      })
     
    }
    
  }

}
</script>
