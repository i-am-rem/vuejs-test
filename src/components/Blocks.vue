<template>
    <div id="blocks" class="container">
        <div class="row" v-if="!isloading">
            <div class="four col-md-6 mt-2 pb-2" v-for="(num, index) in numbers" :key="index">
                <div id="h" class="counter-box"> 
                    <span class="counter">{{ num }}</span>
                </div>
            </div>
        </div>
        <div class="row" v-else>
            <content-loader
                :width="400"
                :height="460"
                :speed="2"
                primaryColor="#f3f3f3"
                secondaryColor="#ecebeb"
            >
                <rect x="2" y="3" rx="2" ry="2" width="173" height="150" /> 
                <rect x="191" y="3" rx="2" ry="2" width="173" height="150" /> 
                <rect x="4" y="165" rx="2" ry="2" width="173" height="150" /> 
                <rect x="192" y="167" rx="2" ry="2" width="173" height="150" />
            </content-loader>
        </div>
    </div>
</template>
<script>
import { ContentLoader } from 'vue-content-loader'

export default {
    components: {
        ContentLoader
    },
    props:{
        numbers: Array
    },
    data(){
        return {
            test: '',
            isloading: true
        }
    },
    created() {
        (this.numbers) ?  setTimeout(() => { this.isloading = false }, 3000) : this.isloading = true;
    }
}
</script>
<style scoped>
 #h:hover {
     background: #41b883;
 }
</style>  