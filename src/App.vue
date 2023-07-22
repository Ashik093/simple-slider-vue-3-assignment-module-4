<script setup>
import { ref } from 'vue';

const sliderData = ref([
  {
    id:1,
    title:"Slider Two",
    image:"images/sliderOne.jpg"
  },
  {
    id:2,
    title:"Slider Three",
    image:"images/sliderTwo.jpg"
  },
  {
    id:3,
    title:"Slider Four",
    image:"images/sliderThree.jpg"
  }
]);

const currentSlide = ref(0);

const nextSlide = () => {
  if (currentSlide.value < sliderData.value.length - 1) {
    currentSlide.value++;
  }else{
    currentSlide.value=0
  }
};

const prevSlide = () => {
  if (currentSlide.value > 0) {
    currentSlide.value--;
  }else{
    currentSlide.value = sliderData.value.length-1
  }
};
</script>

<template>
  <div class="container main-content my-5">
    <div  class="carousel slide card border-0 shadow" >
     
      <div class="carousel-inner card-body">
        
        <div v-for="(item, index) in sliderData" :key="index"  class="carousel-item" :class="currentSlide===index?'active':''">
          <img  :src="item.image" class="d-block w-100 h-100" :alt="item.title">
          <div class="carousel-caption d-none d-md-block">
            <h5>{{item.title}}</h5>
            
          </div>
        </div>
        
        
      </div>
      <div class="m-auto mb-2">
        <strong>{{ currentSlide+1 }} of {{ sliderData.length }} slides</strong>
      </div>
      <button class="carousel-control-prev" type="button" @click="prevSlide" >
        <span class="carousel-control-prev-icon" aria-hidden="true"></span>
        <span class="visually-hidden">Previous</span>
      </button>
      <button class="carousel-control-next" type="button" @click="nextSlide">
        <span class="carousel-control-next-icon" aria-hidden="true"></span>
        <span class="visually-hidden">Next</span>
      </button>
    </div>
  </div>
</template>

<style scoped>

</style>
