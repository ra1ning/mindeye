<template>
	<div class="three">
		<h1 class="slogan">AI驱动世界</h1>
	</div>
</template>
<script>
	function start(){
		var SEPARATION = 100, AMOUNTX = 20, AMOUNTY = 20;
		var three;
		var camera, scene, renderer;
		var particles, particle, count = 0;
		var mouseX = 0, mouseY = 0;
		var windowHalfX = window.innerWidth / 2;
		var windowHalfY = window.innerHeight / 2;
		init();
		animate();
		function init() {
			three = document.querySelector( '.three' );
			camera = new THREE.PerspectiveCamera( 75, window.innerWidth / window.innerHeight, 1, 10000 );
			camera.position.z = 1500;
			camera.position.y = -8000;
			camera.position.x = 8000;
			scene = new THREE.Scene();
			particles = new Array();
			var PI2 = Math.PI * 2;
			var material = new THREE.ParticleCanvasMaterial( {
				color: 0x209fd3,
				program: function ( context ) {
					context.beginPath();
					context.arc( 0, 0, 1, 0, PI2, true );
					context.fill();
				}
			} );

			var i = 0;
			for ( var ix = 0; ix < AMOUNTX; ix ++ ) {
				for ( var iy = 0; iy < AMOUNTY; iy ++ ) {
					particle = particles[ i ++ ] = new THREE.Particle( material );
					particle.position.x = ix * SEPARATION - ( ( AMOUNTX * SEPARATION ) / 2 );
					particle.position.z = iy * SEPARATION - ( ( AMOUNTY * SEPARATION ) / 2 );
					scene.add( particle );
				}
			}
			renderer = new THREE.CanvasRenderer();
			renderer.setSize( window.innerWidth, window.innerHeight );
			three.appendChild( renderer.domElement );
			document.addEventListener( 'mousemove', onDocumentMouseMove, false );
			document.addEventListener( 'touchstart', onDocumentTouchStart, false );
			document.addEventListener( 'touchmove', onDocumentTouchMove, false );
			window.addEventListener( 'resize', onWindowResize, false );
			return renderer.domElement
		}

		function onWindowResize() {
			windowHalfX = window.innerWidth / 2;
			windowHalfY = window.innerHeight / 2;
			camera.aspect = window.innerWidth / window.innerHeight;
			camera.updateProjectionMatrix();
			renderer.setSize( window.innerWidth, window.innerHeight );
		}

		function onDocumentMouseMove( event ) {
			mouseX = event.clientX - windowHalfX;
			mouseY = event.clientY - windowHalfY;
		}

		function onDocumentTouchStart( event ) {
			if ( event.touches.length === 1 ) {
				event.preventDefault();
				mouseX = event.touches[ 0 ].pageX - windowHalfX;
				mouseY = event.touches[ 0 ].pageY - windowHalfY;
			}
		}

		function onDocumentTouchMove( event ) {
			if ( event.touches.length === 1 ) {
				event.preventDefault();
				mouseX = event.touches[ 0 ].pageX - windowHalfX;
				mouseY = event.touches[ 0 ].pageY - windowHalfY;
			}
		}

		function animate() {
			requestAnimationFrame( animate );
			render();
		}

		function render() {
			camera.position.x += ( mouseX - camera.position.x ) * .05;
			camera.position.y += ( - mouseY - camera.position.y ) * .05;
			scene.position.set(0,150,0)
			camera.lookAt( scene.position );
			var i = 0;
			for ( var ix = 0; ix < AMOUNTX; ix ++ ) {
				for ( var iy = 0; iy < AMOUNTY; iy ++ ) {
					particle = particles[ i++ ];
					particle.position.y = ( Math.sin( ( ix + count ) * 0.3 ) * 50 ) + ( Math.sin( ( iy + count ) * 0.5 ) * 50 );
					particle.scale.x = particle.scale.y = ( Math.sin( ( ix + count ) * 0.3 ) + 1 ) * 2 + ( Math.sin( ( iy + count ) * 0.5 ) + 1 ) * 2;
				}
			}

			renderer.render( scene, camera );
			count += 0.1;
		}
	}
	import {THREE} from 'three/index.js'
	import earth from '../assets/earth.png'
	export default{
		data(){
			return {
				earth: earth,
				THREE: THREE
			}
		},
		mounted(){
			start();
		}
	}
</script>
<style scoped>
	.three{
		background: #222;
		width: 100%;
		overflow: hidden;
		position: relative;
		/*background: url(../assets/bannerBG.jpg);*/
		height: 600px;

	}
	@media screen and (max-width: 920px) {
	    .three{
	    	display: none;
	    }
  	}
  	h1{
  		position: absolute;
  		top: 30%;
  		color: #fff;
  		left: 40%;
  		margin: auto;
  		font-size: 60px;
  		font-weight: normal;
  	}
  	img{
		width: 400px;
		height: 400px;
		margin-top: 100px;
		margin-right: 10%
  	}


</style>