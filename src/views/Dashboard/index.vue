<template>
    <div class="dashboard">
        <title-block main-title="Alert innondation !" light-title="Consultez la carte" />
        <Map />
        <title-block class="tips" main-title="Conseils en cas" light-title="de crise majeur :" />
        <div class="card-container">
            <card title="Fermez portes, fenêtres et aérations." img="logo.png" />
            <card title="Coupez le gaz et l’électricité" img="logo.png" />
            <card
                title="Prévoillez une réserve d’eau potable et des lampes de secours."
                img="logo.png"
            />
            <card title="N’allez pas chercher votre enfant à l’école." img="logo.png" />
            <card title="Évitez les déplacements inutiles" img="logo.png" />
            <card title="Essayez de vous informer à l’aide des radios locales" img="logo.png" />
        </div>
        <title-block
            class="tips"
            main-title="Informations utiles"
            light-title="Documents consultables"
        />
    </div>
</template>

<script>
import TitleBlock from '@/components/Title-Bloc'
import Map from '@/components/Map'
import Card from '@/components/Card'

export default {
    name: 'Dashboard',
    components: {
        TitleBlock,
        Map,
        Card,
    },
}
</script>

<style lang="scss" scoped src="./style.scss">
</style>