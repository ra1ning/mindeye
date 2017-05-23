<template>
    <div class="three" @click="show_nav=false">
        <ul :style="show_nav?'height:180px;transition:all 0.3s':'height:0px;transition:all 0.3s'" class="nav" @touchstart="show_nav=false">
            <li><a href="#">业务</a></li>
            <li><a href="#">案例</a></li>
            <li><a href="#">技术</a></li>
            <li><a href="#">我们</a></li>
            <li><a href="#">在线咨询</a></li>
        </ul>
        <div class="hamburger">
            <a @click.stop="show_nav=!show_nav" @touchstart="show_nav=!show_nav"></a>
        </div>
        <h1 class="slogan">AI驱动世界</h1>
    </div>
</template>
<script>
function start() {
    var SEPARATION = 100,
        AMOUNTX = 20,
        AMOUNTY = 20;
    var three;
    var camera, scene, renderer;
    var particles, particle, count = 0;
    var mouseX = 0,
        mouseY = -280;
    var windowHalfX = window.innerWidth / 2;
    var windowHalfY = window.innerHeight / 2;
    init();
    animate();

    function init() {
        three = document.querySelector('.three');
        camera = new THREE.PerspectiveCamera(75, 4 / 2, 1, 10000);
        camera.position.z = 1000;
        camera.position.y = 1000;
        camera.position.x = 1000;
        scene = new THREE.Scene();
        particles = new Array();
        var PI2 = Math.PI * 2;
        var material = new THREE.ParticleCanvasMaterial({
            color: 0x209fd3,
            program: function(context) {
                context.beginPath();
                context.arc(0, 0, 1, 0, PI2, true);
                context.fill();
            }
        });

        var i = 0;
        for (var ix = 0; ix < AMOUNTX; ix++) {
            for (var iy = 0; iy < AMOUNTY; iy++) {
                particle = particles[i++] = new THREE.Particle(material);
                particle.position.x = ix * SEPARATION - ((AMOUNTX * SEPARATION) / 2);
                particle.position.z = iy * SEPARATION - ((AMOUNTY * SEPARATION) / 2);
                scene.add(particle);
            }
        }
        renderer = new THREE.CanvasRenderer();
        renderer.setSize(window.innerWidth, window.innerWidth / 4 * 2);
        three.appendChild(renderer.domElement);
        three.addEventListener('mousemove', onDocumentMouseMove, false);
        three.addEventListener('touchstart', onDocumentTouchStart, false);
        three.addEventListener('touchmove', onDocumentTouchMove, false);
        window.addEventListener('resize', onWindowResize, false);
        return renderer.domElement
    }

    function onWindowResize() {
        windowHalfX = window.innerWidth / 2;
        windowHalfY = window.innerHeight / 2;
        camera.aspect = window.innerWidth / window.innerHeight;
        camera.updateProjectionMatrix();
        renderer.setSize(window.innerWidth, window.innerWidth / 2);
    }

    function onDocumentMouseMove(event) {
        mouseX = event.clientX - windowHalfX;
    }

    function onDocumentTouchStart(event) {
        if (event.touches.length === 1) {
            event.preventDefault();
            mouseX = event.touches[0].pageX - windowHalfX;
        }
    }

    function onDocumentTouchMove(event) {
        if (event.touches.length === 1) {
            event.preventDefault();
            mouseX = event.touches[0].pageX - windowHalfX;
        }
    }

    function animate() {
        requestAnimationFrame(animate);
        render();
    }

    function render() {
        camera.position.x += (mouseX - camera.position.x) * .05;
        camera.position.y += (-mouseY - camera.position.y) * .05;
        scene.position.set(0, 150, 0)
        camera.lookAt(scene.position);
        var i = 0;
        for (var ix = 0; ix < AMOUNTX; ix++) {
            for (var iy = 0; iy < AMOUNTY; iy++) {
                particle = particles[i++];
                particle.position.y = (Math.sin((ix + count) * 0.3) * 50) + (Math.sin((iy + count) * 0.5) * 50);
                particle.scale.x = particle.scale.y = (Math.sin((ix + count) * 0.3) + 1) * 3 + (Math.sin((iy + count) * 0.5) + 1) * 3;
            }
        }

        renderer.render(scene, camera);
        count += 0.1;
    }
}
import {
    THREE
} from 'three/index.js'
import earth from '../assets/earth.png'
export default {
    data() {
            return {
                show_nav: false
            }
        },
        mounted() {
            start();
        }
}
</script>
<style scoped>
.three {
    background: #333;
    width: 100%;
    overflow: hidden;
    position: relative;
}

.hamburger {
    position: absolute;
    display: flex;
    align-items: center;
    justify-content: center;
    height: 100%;
    width: 100%;
    background: url(../assets/logowhite.png) 1.5em 1em no-repeat;
    background-size: 15%;
}

.hamburger img {
    width: 20%;
    height: auto;
}

.hamburger a {
    display: block;
    width: 60px;
    height: 50px;
    position: absolute;
    background: url(../assets/menu.png) no-repeat center center;
    background-size: 40% 40%;
    right: 0;
    top: 0
}

.nav {
    margin: 0;
    padding: 0;
    list-style: none;
    text-align: center;
    overflow: hidden;
    font-size: 20px;
}

.nav li {
    height: 35px;
    line-height: 35px;
    background: #243441;
    font-size: 16px;
}

a {
    color: #fff;
    text-decoration: none;
    cursor: pointer;
}

img {
    width: 400px;
    height: 400px;
    margin-top: 100px;
    margin-right: 10%
}

h1 {
    position: relative;
    color: #fff;
    font-weight: bold;
    text-align: center;
    letter-spacing: 4px;
    margin: 0
}

@media screen and (max-width: 500px) {
    h1 {
        color: #fff;
        top: 90px;
        font-size: 18px;
    }
}

@media screen and (min-width: 500px) and (max-width: 920px) {
    h1 {
        color: #fff;
        top: 150px;
        font-size: 38px;
    }
}

@media screen and (min-width: 920px) {
    h1 {
        color: #fff;
        top: 250px;
        font-size: 48px;
    }
    .hamburger {
        display: none;
    }
}
</style>
