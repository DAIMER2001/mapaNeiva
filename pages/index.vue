<template>
  <div>
    <Navbar></Navbar>

    <b-container class="mt-5">

    <Leaflet></Leaflet>

    </b-container>
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