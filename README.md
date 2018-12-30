# vue-longdo-map

vue-longdo-map เป็น simple component wrapper ที่ในเวอร์ชันปัจจุบันยังรองรับเฉพาะ Overlay ที่เป็น Maker และ Popup ตัว Library รองรองรับการ costom component เพื่อให้รองรับคุณสมบัติได้เอง สามารถดูตัวอย่างการสร้าง component เพิ่มเติมได้จาก component /components/LongoMapPopup.vue

# การใช้งานเบื้องต้น
## ติดตั้ง
```
npm i vue-longdo-map
```
## การเรียกใช้
ลงทะเบียนกับทาง Longdo Map และสร้าง API Key เพื่อนำมาใช้งาน โดยหน้าการสร้าง API Key ให้ไปที่เมนู **My Londo Map** > **Longdo Map API** 
[https://map.longdo.com/user/{{user_id}}](https://map.longdo.com/user/{{user_id}})
```html
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

				<LongdoPopup
					v-for="popup in popups"
					:popup="popup"
					:map="map"></LongdoPopup>
			</template>
		</LongdoMap>
	</div>
</template>
```
```javascript
<script>
import { LongdoMap, LongdoMapMarker, LongdoMapPopup}  from 'vue-longdo-map'

export default {
  name: 'app',
  components: {
    LongdoMap,
    LongdoMapMarker,
    LongdoMapPopup
	},
	data:{
		map: {
			apiKey: 'xxxxxxxxxxxxxxx' // API Key
			center: {
				lon: 100,
				lat: 16
			}
		}
	}
}
```
# การเพิ่ม component
ในกรณ๊ที่ต้องการ custom component อื่นของ map ขึ้นมาใหม่ ภายใต้ component นั้นให้เตรียม props ไว้ในในชื่อ map ที่มี type เป็นแบบ Promise ดังนั้นเมื่อเรียกใช้ component ใหม่ให้เรียกใช้เป็น child ของ component <LongdoMap>
```html
<LongdoMap>
	<template scope="{map}">
		<LongdoMapCostomComponent :map="map"></LongdoMapCostomComponent>
	</template>
</LongdoMap>
```
# ทดลองติดตั้งในเครื่อง
```
git clone git@github.com:zupaazhai/vue-longdo-map.git
cd vue-longdo-map
npm install
```
# ข้อมูลเพิ่มเติม
Longdo Map API Reference ([http://api.longdo.com/map/doc/content/](http://api.longdo.com/map/doc/content/))
Longdo Map Demo ([http://api.longdo.com/map/doc/](http://api.longdo.com/map/doc/))