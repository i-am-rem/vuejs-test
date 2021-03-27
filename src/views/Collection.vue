
<template>
  <div class="home">
   <div class="container">
     <div class="row">
        <div v-if="!isloading" class="container-fluid py-5 col-lg-4">
          <h1 class="display-5 fw-bold">{{ title }}</h1>
          <p class="col-md-8 fs-4">
            <span v-if="!readMoreActivated">{{ description.slice(0, 150) }}</span>
            <a class="" v-if="!readMoreActivated" @click="activateReadMore" href="#">
               Read more...
            </a>
            <span v-if="readMoreActivated" v-html="description"></span>
          </p>
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
import mockData from '@/fixtures/pxtqu8tf3c69m4wus0t9s8wzt.json'

export default {
  name: 'Collection',
  components: {
    Counter,
    ContentLoaderComponent
  },
  data() {
    return {
      randomNumbers:[],
      title:"",
      description: "",
      isloading: true,
      readMoreActivated: false
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
        (mockData) ?  
          setTimeout(() => {
            this.isloading = false
            this.title = mockData.title
            this.description = mockData.description
            this.randomNumbers = mockData.blocks.map(numbers => numbers.value)
          }, 3000) 
        : this.isloading = false;
    },
    /* read more function */
    activateReadMore(){
      this.readMoreActivated = true;
    },
    
  }

}
</script>
