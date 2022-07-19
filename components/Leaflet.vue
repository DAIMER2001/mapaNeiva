<template>
  <div>
      <b-card bg-variant="dark" header="Mapa Neiva" text-variant="white" class="text-center">

        <div id="map-wrap" style="height: 80vh; width: 100%;">
        <no-ssr>
            <l-map :zoom="13" :center="[2.9251045,-75.298481]">
            <l-tile-layer url="http://{s}.tile.osm.org/{z}/{x}/{y}.png"></l-tile-layer>
            <l-marker v-for=" marcador in marcadores " :lat-lng="marcador">
            <l-popup>Hello!</l-popup>
            </l-marker>
            </l-map>
        </no-ssr>
        </div>

      </b-card>

      <button class="btn btn-red" @click="modificarMarcadores"> MODIFICAR MARCADORES</button>

      {{marcadores}}
  </div>
</template>
<script>

export default {
    data()  {
        return {
            marcadores: [
                    [2.9251045,-75.298481],
                    [2.9270576,-75.2855848],
            ]
        }
    },
  mounted() {
    
    
  },
  methods: {
      modificarMarcadores() {
        this.marcadores = [
                    [2.9251111,-75.2944444],
                    [2.9270222,-75.2850000],
            ]
      }
  }
};
</script>