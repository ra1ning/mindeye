<template>
    <div id="app">
        <router-view></router-view>
    </div>
</template>
<script>
export default {
    mounted() {
        window.proportion = 10 / 1366;
        if (window.innerWidth < 1366) {
            document.querySelector('html').style.fontSize = window.innerWidth * window.proportion + 'px';
        }
        window.addEventListener('resize', function() {
            if (window.innerWidth < 1366) {
                document.querySelector('html').style.fontSize = window.innerWidth * window.proportion + 'px';
            }
        })
    }
}
</script>
<style>
#app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: right;
    color: #2c3e50;
}

body {
    margin: 0 auto;
    font-family: "微软雅黑,宋体"!important;
    font-size: 16px;
}

html {
    font-size: 10px;
}
</style>
