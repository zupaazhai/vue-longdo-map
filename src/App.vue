<template>
  <div id="app">
    <LongdoMap :center="map.center" :apiKey="map.apiKey">
      <template slot-scope="{ map }">
        <LongdoMapMarker
          :map="map"
          @click="onClickMarker"
          @move="onMoveMarker"
          @hover="onHoverMarker"
          @change="onChageMarker"
          v-for="marker in markers"
          :marker="marker"></LongdoMapMarker>

        <LongdoMapPopup
          v-for="popup in popups"
          :popup="popup"
          :map="map"></LongdoMapPopup>
      </template>
    </LongdoMap>
  </div>
</template>

<script>
import LongdoMap from './components/LongdoMap.vue'
import LongdoMapMarker from './components/LongdoMapMarker.vue'
import LongdoMapPopup from './components/LongdoMapPopup.vue'

export default {
  name: 'app',
  components: {
    LongdoMap,
    LongdoMapMarker,
    LongdoMapPopup
  },
  data: () => {
    return {
      map: {
        apiKey: process.env.VUE_APP_API_KEY,
        center: {
          lon: 100,
          lat: 16
        },
      },
      markers: [
        {
          id: 1,
          location: {
            lon: 100,
            lat: 16
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
          id: 2,
          location: {
            lat: 18,
            lon: 98
          }
        },
        {
          id: 3,
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
      ],
      popups: [
        {
          id: 1,
          location: {
            lat: 20,
            lon: 99
          },
          detail: {
            title: 'Popup',
            detail: 'Popup detail...',
            size: { width: 200, height: 200 },
            closable: false
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
      console.log('hover')
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
