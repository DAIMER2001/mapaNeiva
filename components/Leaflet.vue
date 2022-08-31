<template>
  <div v-if="isLoadSensor" id="map-wrap" style="height: 88vh; min-width: 100%; max-width: 100%;">
    <no-ssr>
      <l-map :zoom="13" :center="[2.9251045, -75.298481]">
        <l-tile-layer
          url="http://{s}.tile.osm.org/{z}/{x}/{y}.png"
        ></l-tile-layer>
        <l-marker v-for="data in sensors" :lat-lng="data.gps">
          <l-icon
            :icon-size="dynamicSize"
            :icon-anchor="dynamicAnchor"
            :icon-url="iconColors[data.sensor.color]"
          >
          </l-icon>

          <l-popup>
            <h2>{{ data.sensor.category }}</h2>
          </l-popup>
        </l-marker>
      </l-map>
    </no-ssr>
  </div>
</template>
<script>

// import L from 'leaflet';

import imgRojo from "../static/images/nube_Rojo.png"
import imgPurpura from "../static/images/nube_Purpura.png"
import imgNaranja from "../static/images/nube_Naranja.png"
import imgVerde from "../static/images/nube_Verde.png"
import imgAmarillo from "../static/images/nube_Amarillo.png"
import imgMarron from "../static/images/nube_Marron.png"

export default {
  data() {
    return {
      sensors: [
        {
          address: "Carrera 2 con calle 8 (Centro Comercial los Comuneros)",
          gps: [2.9261902, -75.2923712],
          id: 1,
          ica: 51,
          sensor: {},
        },
        {
          address: "Carrera 4 con calle 4 (Zona de talleres de motos)",
          gps: [2.9232141, -75.2903041],
          id: 2,
          ica: 111,
          sensor: {},
        },
        {
          address: "Carrera 7 entre calles 11 y 12 (Clinica Medilaser)",
          gps: [2.9306394, -75.2904968],
          id: 3,
          ica: 222,
          sensor: {},
        },
        {
          address: "Carrera 5 con calle 10 (Alcaldía Municipal)",
          gps: [2.9289054, -75.2897672],
          id: 4,
          ica: 333,
          sensor: {},
        },
      ],
      icaColors: [
        { rangeStart: 0, rangeEnd: 50, color: "Verde", category: "Buena" },
        {
          rangeStart: 51,
          rangeEnd: 100,
          color: "Amarillo",
          category: "Aceptable",
        },
        {
          rangeStart: 101,
          rangeEnd: 150,
          color: "Naranja",
          category: "Dañina a la salud de Grupos Sensibles",
        },
        {
          rangeStart: 151,
          rangeEnd: 200,
          color: "Rojo",
          category: "Dañina a la salud",
        },
        {
          rangeStart: 201,
          rangeEnd: 300,
          color: "Purpura",
          category: "Muy dañina a la salud",
        },
        {
          rangeStart: 301,
          rangeEnd: 500,
          color: "Marron",
          category: "Peligrosa",
        },
      ],
      iconColors: {
        Marron: imgMarron,
        Rojo: imgRojo,
        Verde: imgVerde,
        Amarillo: imgAmarillo,
        Purpura: imgPurpura,
        Naranja: imgNaranja
      },
      isLoadSensor: false,
      iconSize: 64
    };
  },
  computed: {
    dynamicSize() {
      return [this.iconSize, this.iconSize * 1.15];
    },
    dynamicAnchor() {
      return [this.iconSize / 2, this.iconSize * 1.15];
    },
  },
  mounted() {
    this.getMarkers();
  },
  methods: {
    async getMarkers() {
      this.sensors.forEach((dataSensor) => {
        this.icaColors.forEach((range) => {
          if (
            dataSensor.ica >= range.rangeStart &&
            dataSensor.ica <= range.rangeEnd
          ) {
            dataSensor.sensor = range;
          }
        });
      });
      this.isLoadSensor = true;
    },
  },
};
</script>
