<template>
    <div ref="map" id="map"></div>
</template>

<script>
import { map, tileLayer, marker } from 'leaflet'

export default {
    name: 'Map',
    data() {
        return {
            map: undefined,
        }
    },
    mounted() {
        this.map = map('map').setView(
            [43.80478427040863, 4.658995550125838],
            15,
        )

        tileLayer(
            'https://{s}.basemaps.cartocdn.com/rastertiles/voyager/{z}/{x}/{y}{r}.png',
            {
                attribution:
                    '&copy; <a href="https://www.openstreetmap.org/copyright">OpenStreetMap</a> contributors &copy; <a href="https://carto.com/attributions">CARTO</a>',
                subdomains: 'abcd',
                maxZoom: 25,
            },
        ).addTo(this.map)

        this.addMarker(43.80478427040863, 4.658995550125838)
    },
    methods: {
        addMarker(lat, lng) {
            const markerEl = marker([lat, lng])
            markerEl.addTo(this.map)
            markerEl.on('click', e => {
                console.log(e)
            })
        },
    },
}
</script>

<style lang="scss" scoped src="./index.scss"></style>