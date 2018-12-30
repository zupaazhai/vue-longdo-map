<template>
  <div></div>
</template>

<script>
export default {
  props: {
    map: Promise,
    popup: {
      type: Object,
      required: true
    }
  },
  name: 'LongdoMapPopup',
  created: function () {

    this.map.then(map => {

      let detail = this.popup.detail ? this.popup.detail : {},
        location = this.popup.location ? this.popup.location : {}

      var popup = new longdo.Popup(location, detail)

      map.Overlays.add(popup)
    })
  }
}
</script>
