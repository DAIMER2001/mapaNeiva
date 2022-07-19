<template>
  <div>
    <Navbar></Navbar>

    <b-container class="mt-5">

        <h4>Video contaminación ambiental en Neiva </h4>

        <youtube :video-id="video1" ref="youtube"></youtube>


       <div class="p-5 mt-4">
<h3>video dioxido de carbono</h3>
     <youtube :video-id="name2" ref="youtube1"></youtube>

      </div> 
       

    </b-container>
  </div>
</template>
<script>
import Navbar from '../components/Navbar.vue';

export default {
    
  data: function() {
  return {
        video1:'AwGIcyD6iSU',
        name2 :'yge_O0UCYcM'
    };
    
  },
    mounted() {
        this.player.playVideo()
    },
    components: {  Navbar },
  computed: {
    player() {
      return this.$refs.youtube.player
    }
  }

};
</script>