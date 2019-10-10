<template>
    <div class="danger-page-container">
        <div class="danger-container">
            <title-bloc
                :mainTitle="lang == 'fr' ? 'Les risques' : 'The main'"
                :lightTitle="lang == 'fr' ? 'majeurs' : 'dangers'"
            />
            <div class="danger-list">
                <!-- Include danger grid here -->
            </div>
        </div>
        <div class="service-container">
            <title-bloc
                :mainTitle="lang == 'fr' ? 'Service d\'alerte' : 'Alert service'"
                :lightTitle="lang == 'fr' ? 'téléphonique' : 'hotline'"
            />
            <div class="service-text">
                <p class="text">{{ data.danger.service.text[lang] }}</p>
                <input type="button" :value="data.danger.service.button" class="button" />
            </div>
        </div>
    </div>
</template>

<script>
import data from '../../data.json'
import TimelineCard from '@/components/Timeline-Card'
import TitleBloc from '@/components/Title-Bloc'

export default {
    name: 'Danger',
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