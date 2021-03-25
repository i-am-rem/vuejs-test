<template>
    <div id="collections">
        <div class="container">
            <div v-if="!isloading" class="row row-cols-1 row-cols-sm-2 row-cols-md-3 g-3">
                <div class="col" v-for="(collection, index) in collections" :key="index">
                    <card :content="collection.content"></card>
                </div>
            </div>
            <div v-else class="row row-cols-1 row-cols-sm-2 row-cols-md-3 g-3">
                <collections-loader></collections-loader>
                <collections-loader></collections-loader>
                <collections-loader></collections-loader>
            </div>
        </div>
    </div>
</template>
<script>
import axios from 'axios'
import Card from '@/components/Card.vue'
import CollectionsLoader from '@/components/CollectionsLoader.vue'

export default {
    components: {
        Card,
        CollectionsLoader
    },
    data() {
        return {
            isloading: true,
            collections:[]
        }
    },
    created() {
        this.getCollections()
    },
    methods: {
        /**
        * sets the title & the description
        * */ 
        async getCollections() {
            const content =  axios.get('/static.json')
            await content.then(response => {
                console.log(response)
                let delay = (response.data.collections && response.data.collections.length > 0 ) ?  
                    setTimeout(() => {
                        this.isloading = false
                        this.collections = response.data.collections
                    }, 3000) 
                    : this.isloading = true;
                delay
            }).catch(error => {
                console.log(error)
                this.isloading = false
            })
            
        }
    }
    
}
</script>  