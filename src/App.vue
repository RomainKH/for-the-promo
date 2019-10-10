<template>
    <div id="app">
        <Topbar :data="data.header" />
        <div class="container">
            <component :is="getComponent" />
        </div>
    </div>
</template>

<script>
import data from './data.json'

import Alert from './components/Alert'
import Home from './views/Home'
import Map from './components/map'
import Topbar from './components/Header'

export default {
    name: 'App',
    components: {
        Home,
        Map,
        Alert,
        Topbar,
    },
    data() {
        return { lang: 'fr', route: '/' }
    },
    created() {
        const [lang, route] = this.parseRoute()
        this.lang = lang
        this.route = route
        this.data = data
    },
    mounted() {
        document.documentElement.style.setProperty(
            '--basic-color',
            data.colors.basicColor,
        )
        document.documentElement.style.setProperty(
            '--light-color',
            data.colors.lightColor,
        )
        document.documentElement.style.setProperty(
            '--accent-color',
            data.colors.accentColor,
        )
    },
    computed: {
        getComponent() {
            let component = 'Home'
            switch (this.route) {
                case 'map':
                    component = 'Map'
                    break

                case 'alert':
                    component = 'Alert'
                    break

                default:
                    break
            }

            return component
        },
    },
}
</script>
<style lang="scss">
@import '@/components/App/Reset.scss';
@import '@/components/App/App.scss';

.topbar {
    position: fixed;
    width: 100%;
    height: 60px;
    background: #fff;
    text-align: center;
    display: flex;
    justify-content: center;
    align-items: center;
}

.container {
    padding-top: 100px;
}
</style>
