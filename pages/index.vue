<template>
  <div>
    <Navbar></Navbar>

    <Leaflet></Leaflet>
  </div>
</template>
<script>
import Leaflet from '../components/Leaflet.vue';
import Navbar from '../components/Navbar.vue';

export default {
    mounted() {
    },
    components: { Leaflet, Navbar }
};
</script>