<template>
    <div class="alert-page-container">
        <div class="media-container">
            <title-bloc
                :mainTitle="lang == 'fr' ? 'Les médias' : 'Media'"
                :lightTitle="lang == 'fr' ? 'à suivre' : 'to follow'"
            />
            <div class="media-list">
                <a
                    class="media-item"
                    v-for="media in data.alert.media"
                    :key="media.id"
                    :href="media.link"
                    target="_blank"
                >
                    <img
                        class="item-image"
                        :src="require('../../assets/' + media.image.src)"
                        :alt="media.image.alt"
                    />
                </a>
            </div>
        </div>
        <div class="timeline-container">
            <title-bloc
                :mainTitle="lang == 'fr' ? 'Alerte inondation !' : 'Flood alert!'"
                :lightTitle="lang == 'fr' ? 'Historique' : 'History'"
            />
            <timeline-card
                v-for="timeline in data.alert.historic"
                :key="timeline.id"
                :data="timeline"
                :lang="lang"
            />
        </div>
    </div>
</template>

<script>
import data from '../../data.json'
import TimelineCard from '@/components/Timeline-Card'
import TitleBloc from '@/components/Title-Bloc'

export default {
    name: 'Alert',
    components: {
        'timeline-card': TimelineCard,
        'title-bloc': TitleBloc,
    },
    created() {
        const [lang, route] = this.parseRoute()
        this.lang = lang
        this.route = route
        this.data = data
    },
    mounted() {},
}
</script>

<style scoped lang="scss">
@import 'style.scss';
</style>