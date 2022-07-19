<template>
  <div>
    <Navbar></Navbar>

    <b-container class="mt-5">
    <carousel />


    <img  src="@/assets/images/oso_polar1.jpeg" width="350" height="350"/>

        <h4>Imagenes</h4>

    </b-container>
  </div>
</template>
<script>
import Navbar from '../components/Navbar.vue';
import carousel from '../components/carousel.vue';

import img from "@/assets/images/oso_polar1.jpeg"
export default {
     data: function() {
  return {
        img: img
    };
    
  },
    components: {  Navbar }
};

</script>



