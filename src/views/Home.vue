<template>
    <div id="collections" >
        <div aria-live="polite" aria-atomic="true" class="container">
          <div class="form-floating pb-3">
            <textarea class="form-control" v-model="text" placeholder="Leave a comment here" id="floatingTextarea2" style="height: 100px"></textarea>
            <label for="floatingTextarea2">Type text here to post...</label>
          </div>
          <!-- cards -->
          <button type="button" class="btn btn-outline-primary" :disabled="!text" v-on:click="submitText">Post now</button>
            <div v-if="!isloading" class="row row-cols-1 row-cols-sm-2 row-cols-md-3 g-3">
                <div class="col" v-for="(collection, index) in collections" :key="index">
                    <card :content="collection.content" v-on:deletePostEvent="deletePost" :keyId="index"></card>
                </div>
            </div>
            <!-- loader -->
            <div v-else class="row row-cols-1 row-cols-sm-2 row-cols-md-3 g-3 pt-3">
                <collections-loader></collections-loader>
                <collections-loader></collections-loader>
                <collections-loader></collections-loader>
            </div>
          
           <!-- Then put toasts within -->
            <div class="toast-container position-absolute top-0 end-0 p-3">
              <div class="toast" role="alert" id="liveToast" aria-live="assertive" aria-atomic="true">
                <div class="toast-header">
                  <strong class="me-auto">Toast</strong>
                  <small>Just now</small>
                  <button type="button" class="btn-close" data-bs-dismiss="toast" aria-label="Close"></button>
                </div>
                <div class="toast-body">
                  Congrats! your note has been posted
                </div>
              </div>
            </div>
          <!--  -->
        </div>
    </div>
</template>
<script>
import mockData from '@/fixtures/pxtqu8tf3c69m4wus0t9s8wzt.json'
import Card from '@/components/Card.vue'
import CollectionsLoader from '@/components/CollectionsLoader.vue'
import { Toast } from 'bootstrap'

export default {
  name: 'Home',
    components: {
        Card,
        CollectionsLoader
    },
    data() {
        return {
            isloading: true,
            collections:[],
            text:""
        }
    },
    created() {
        this.getCollections()
    },
    methods: {
        /**
        * sets the title & the description
        * */ 
        getCollections() {
            (mockData.collections && mockData.collections.length > 0 ) ?  
                setTimeout(() => {
                    this.isloading = false
                    this.collections = mockData.collections
                }, 3000) 
                : this.isloading = false;
            
        },
        /* post a content */
        submitText() {
          this.collections.push({content:this.text})
          this.text = ''
          let myToast = new Toast(document.getElementById('liveToast'))
          myToast.show()
        },
        /* delete post */
        deletePost(e) {
          console.log("DELETE!!", e)
          this.collections.splice(e.index, 1)
        }
    }
    
}
</script>  