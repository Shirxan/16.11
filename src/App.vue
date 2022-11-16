<script setup>
import SectionVue from './components/Section.vue'
import axios from 'axios'
</script>

<template>
  <div>
    <SectionVue :products="products"/>
    </div>
</template>

<script>
export default{
  data(){
    return{
      products : []
    }
  },
  created() {
   this.axios.get('https://fakestoreapi.com/products').then(({data}) =>{
    this.products=data
   })
  },
}
</script>
