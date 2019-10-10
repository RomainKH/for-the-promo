<template>
    <div id="app">
        <header class="topbar">
            <img src="./assets/logo.png" alt="logo" />
        </header>
        <div class="container">
            <component :is="getComponent" />
        </div>
    </div>
</template>
<script>
import Home from './views/Home'
import Map from './components/map'

export default {
    name: 'App',
    components: {
        Home,
        Map,
    },
    data() {
        return { lang: 'fr', route: '/' }
    },
    created() {
        const [lang, route] = this.parseRoute()
        this.lang = lang
        this.route = route
    },
    computed: {
        getComponent() {
            let component = 'Home'
            switch (this.route) {
                case 'map':
                    component = 'Map'
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
    padding: 0px 10px;
}
</style>
