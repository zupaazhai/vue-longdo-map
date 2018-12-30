<template>
  <div></div>
</template>

<script>
export default {
  props: {
    map: Promise
  },
  name: 'LongdoPopup',
  created: function () {
    this.map.then(map => {
      map.Overlays.add(new longdo.Popup({ lon: 100, lat: 16 }, {
        title: 'Popup',
        detail: 'Simple popup'
      }))
    })
  }
}
</script>
