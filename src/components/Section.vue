<script setup>
import axios from 'axios';
</script>
<template>
    
      
<div class="album py-5 bg-light">
  <div class="container">

    <div class="row row-cols-1 row-cols-sm-2 row-cols-md-3 g-3">
      <div v-for="item in products " :key="item.id" class="col">
        <div class="card shadow-sm">
       <img :src="item.image" alt="" class="img-fluid custom-img">

          <div class="card-body">
            <p class="card-text">{{item.title}}</p>
            <div class="d-flex justify-content-between align-items-center">
              <div class="btn-group">
                <button  type="button" class="btn btn-sm btn-outline-secondary"  data-bs-toggle="modal" data-bs-target="#exampleModal" @click="gonder(item.id)">View</button>
             
              </div>
              <small class="text-muted">{{item.price}}$</small>
            </div>
          </div>
        </div>
      </div>



    </div>
  </div>
</div>
<div class="modal fade" id="exampleModal" tabindex="-1" aria-labelledby="exampleModalLabel" aria-hidden="true">
  <div class="modal-dialog">
    <div class="modal-content">
      <div class="modal-header">
        <h1 class="modal-title fs-5" id="exampleModalLabel">Modal title</h1>
        <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
      </div>
      <div v-if="double.description" class="modal-body">
        <p>Title:{{double.title}}</p>
       <p>Description: {{double.description}}</p>
       <p> Count:{{double.rating.count}}</p>
       <p>Category: {{double.category}}</p>

       
        <i v-for="ulduz in Math.round(double.rating.rate) " :key="ulduz" class="fa-solid fa-star"></i>  
        <i v-if="double.rating.rate!=Math.round(double.rating.rate)" class="fa-solid fa-star-half"></i>
        
      
      
      </div>
      <div class="modal-footer">
        <button type="button" class="btn btn-secondary" data-bs-dismiss="modal">Close</button>
        <button type="button" class="btn btn-primary">Save changes</button>
      </div>
    </div>
  </div>
  </div>
</template>







<script>
export default {
  data(){
   return{
    double:{}
   } 
  } , 
    props:{
    products:{
        type: Array
    }

    },
    methods:{
        gonder(id){
            this.axios.get('https://fakestoreapi.com/products/' + id).then(({data}) =>{
               this.double=data
          })
        }
    },
    
  
}
</script>