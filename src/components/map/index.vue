<template>
    <div id="map"></div>
</template>

<script>
import data from '../../data.json'
import { map, tileLayer, marker, icon } from 'leaflet'

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

        this.addMarker(...data.dashboard.map.townLatLng)

        data.dashboard.map.incidentLatLngs.forEach(incident => {
            this.addMarker(...incident.latLng)
            const [lang, _] = this.parseRoute()
            console.log(this.translate(incident.description))
        })
    },
    methods: {
        addMarker(lat, lng) {
            const iconEl = icon({
                iconUrl:
                    'data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAACgAAAAoBAMAAAB+0KVeAAAAElBMVEVHcEwac+gac+gac+gac+gac+gtu67uAAAABnRSTlMAV+n+gxT6zFvXAAAAlElEQVR4AWKAAyFFQNn0doIwDABQtIUOIGQEJ7AZQfx3/2ksePEgyefl5AnZlrHPeVvimPOxwomC10BBFERBFERBdIEo+ETBA7Xihg4xGixGg6/vStHguxgdTRQvehebPs9ftNE8m148uupe7PA9yhCDHb4Y7JrF4P89QS8CoiAKoiAKrhREQRREQRREV7h+hOXLfACI4EsohCj6BwAAAABJRU5ErkJggg==',
                iconSize: [40, 40],
                iconAnchor: [20, 40],
            })

            const markerEl = marker([lat, lng], { icon: iconEl })
            markerEl.addTo(this.map)
            markerEl.on('click', e => {
                console.log(e)
            })
        },
    },
}
</script>

<style lang="scss" scoped src="./index.scss"></style>