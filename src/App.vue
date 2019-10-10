<template>
    <div id="app">
        <Topbar :data="data" />
        <div class="container">
            <component :is="getComponent" />
        </div>
        <Navbar :route="route" :lang="lang" />
    </div>
</template>

<script>
import data from './data.json'

import Danger from './views/Danger'
import Home from './views/Home'
import Alert from './views/Alert'
import Error404 from './views/404'
import Dashboard from './views/Dashboard/index'

import Navbar from './components/Nav-Bar'
import Topbar from './components/Header'

export default {
    name: 'App',
    components: {
        Home,
        Dashboard,
        Alert,
        Topbar,
        Error404,
        Danger,
        Navbar,
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
                case '':
                    break
                case 'dashboard':
                    component = 'Dashboard'
                    break

                case 'alert':
                    component = 'Alert'
                    break

                case 'danger':
                    component = 'Danger'
                    break

                default:
                    component = 'Error404'
                    break
            }

            return component
        },
    },
    watch: {
        $route() {
            const [lang, route] = this.parseRoute()
            this.lang = lang
            this.route = route
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
    padding: 0 10px;
    padding-top: 100px;
}
</style>
