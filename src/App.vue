<template>
  <div id="app">
    <LongdoMap :center="map.center" :apiKey="map.apiKey">
      <template slot-scope="{ map }">
        <LongdoMapMarker
          @click="onClickMarker"
          @move="onMoveMarker"
          @hover="onHoverMarker"
          @change="onChageMarker"
          v-for="marker in markers"
          :marker="marker"
          :map="map"></LongdoMapMarker>
      </template>
    </LongdoMap>
  </div>
</template>

<script>
import LongdoMap from './components/LongdoMap.vue'
import LongdoMapMarker from './components/LongdoMapMarker.vue'
import LongdoPopup from './components/LongdoPopup.vue'

export default {
  name: 'app',
  components: {
    LongdoMap,
    LongdoMapMarker,
    LongdoPopup
  },
  data: () => {
    return {
      map: {
        apiKey: 'c85040ce6273322881a3f0461d7c2e82',
        center: {
          lon: 100,
          lat: 16
        },
      },
      markers: [
        {
          location: {
            lon:100,
            lat: 16,
          },
          detail: {
            title: 'Marker',
            icon: {
              url: 'https://map.longdo.com/mmmap/images/pin_mark.png',
              offset: { x: 12, y: 45 }
            },
            detail: 'Drag me',
            visibleRange: { min: 7, max: 9 },
            draggable: true
          }
        },
        {
          location: {
            lat: 18,
            lon: 98
          }
        },
        {
          location: {
            lat: 18,
            lon: 99
          },
          detail: {
            icon: {
              url: 'https://map.longdo.com/mmmap/images/pin_mark.png',
              offset: { x: 12, y: 45 }
            }
          }
        }
      ]
    }
  },
  methods: {
    changeCenter: function () {
      this.map.center = {
        lat: 18.7716998,
        lon: 98.816391
      }
    },
    onClickMarker: function (marker) {
      console.log('click')
    },
    onMoveMarker: function (marker) {
      console.log('move')
    },
    onHoverMarker: function (marker) {
      console.log('Hover')
    },
    onChageMarker: function (marker) {
      console.log('change')
    }
  }
}
</script>

<style lang="scss">
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
