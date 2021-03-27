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
import mockData from '@/fixtures/pxtqu8tf3c69m4wus0t9s8wzt.json'
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
        getCollections() {
            (mockData.collections && mockData.collections.length > 0 ) ?  
                setTimeout(() => {
                    this.isloading = false
                    this.collections = mockData.collections
                }, 3000) 
                : this.isloading = false;
            
        }
    }
    
}
</script>  