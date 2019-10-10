<template>
    <div class="timeline-item">
        <div class="item-date">
            <span class="date-day">{{ data.date.day }}.</span>
            <span class="date-month">{{ data.date.month }}</span>
            <span class="date-bar-spacing"></span>
        </div>
        <div class="item-info-container">
            <p class="info-text">
                <span class="text-hour">{{ data.date.hour }} :</span>
                {{ data.text }}
            </p>
            <a :href="data.link" class="info-link" target="_blank">En savoir +</a>
            <img
                class="info-thumbnail"
                :src="data.image.src"
                :alt="data.image.alt"
                v-if="data.image"
            />
        </div>
    </div>
</template>

<script>
export default {
    name: 'TimelineCard',
    data() {
        return {
            data: {
                date: {
                    hour: '20h30',
                    day: '09',
                    month: '10',
                },
                text:
                    'Classifieds are usually the first place you think of when you are getting ready to make a purchase. Whether you want to purchase a vehicle, bed, or pet',
                link: 'https://mescouilles.fr',
                image: {
                    src: '/images/',
                    alt: 'Image test',
                },
            },
        }
    },
}
</script>

<style lang="scss" scoped>
@import 'style.scss';
</style>
