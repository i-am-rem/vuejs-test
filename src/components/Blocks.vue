<template>
    <div id="blocks" class="container">
        <div class="row" v-if="!isloading">
            <div class="four col-md-6 mt-2 pb-2" v-for="(num, index) in numbers" :key="index">
                <div id="h" class="counter-box" v-bind:class="{ 'purple': num == 100, 'grey' : num == 0 }"> 
                    <span class="counter" v-on:click="setBlockValue(num, index)" >{{ num }}</span> 
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
        <my-modal :modalId="'exampleModal'" ></my-modal>
        

    </div>
</template>
<script>
import { ContentLoader } from 'vue-content-loader'
import { Modal } from 'bootstrap'
import MyModal from '@/components/Modal.vue'

export default {
    components: {
        ContentLoader,
        MyModal
    },
    props:{
        numbers: Array
    },
    data(){
        return {
            test: '',
            isloading: true,
            number:100,
            index:''
        }
    },
    created() {
        (this.numbers) ?  setTimeout(() => { this.isloading = false }, 3000) : this.isloading = true;
    },
    methods:{
        /* opens modal when completed block is 100 */
        setBlockValue(num, index) {
            let value = (num == 100 ) ? 0 : 100;
            this.numbers.splice(index,1, value);
            let modal = new Modal(document.getElementById('exampleModal'));
            let equal = this.numbers.every((val, i, arr) => val === arr[0] && val == 100 );
            (equal) ? modal.show() : ''
            
        }
    }
}
</script>
<style scoped>
 #h:hover {
    background: #41b883;
 }
 .purple{
     background: #5c3c92;
 }
 .grey{
     background: rgb(248, 248, 248);
 }
</style>  