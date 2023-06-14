## Get Started with [Three.js](https://threejs.org/)

A brief description of starting your own three.js project.

For detailed version read this [three.js documentaion](https://threejs.org/docs/index.html#manual/en/introduction/Creating-a-scene)
# How to build a 3d scene using three.js
 Start a vite project by
```bash
npm create vite@latest
```
Choose Vanilla JS and remove all the default code

Open the project file in integrated termial and install threejs by

```bash
npm install three
```
Add canvas to the body
```HTML
<canvas id="bg"></canvas>
```
Style the canvas as
```CSS
canvas {
  position: fixed;
  top: 0;
  left: 0;
}
```
Now import threejs in javascript
```javascript
import * as THREE from 'three';
```
To start things we always need three objects
1) Scene
2) Camera
3) Renderer

```javascript
const scene = new THREE.Scene();
const camera = new THREE.PerspectiveCamera( 75, window.innerWidth / window.innerHeight, 0.1, 1000 );

const renderer = new THREE.WebGLRenderer({
  canvas: document.querySelector('#bg'),
});
renderer.setSize( window.innerWidth, window.innerHeight );
document.body.appendChild( renderer.domElement );
```

Add objects as geometry
```javascript
const geometry = new THREE.BoxGeometry( 1, 1, 1 );
const material = new THREE.MeshBasicMaterial( { color: 0x00ff00 } );
const cube = new THREE.Mesh( geometry, material );
scene.add( cube );

camera.position.z = 5;
```
Add light
```js
const pointLight = new THREE.PointLight(0xffffff);
pointLight.position.set(5, 5, 5);

const ambientLight = new THREE.AmbientLight(0xffffff);
scene.add(pointLight, ambientLight);
```
Rendering the scene
```javascript
function animate() {
	requestAnimationFrame( animate );
	renderer.render( scene, camera );
}
animate();
```
Animate the object
```js
cube.rotation.x += 0.01;
cube.rotation.y += 0.01;
```
Add gridHelper
```js
const gridHelper = new THREE.GridHelper( 200, 50 );
scene.add( gridHelper );
```
To view the whole scene by controlling the mouse import OrbitControl in js
```js
import { OrbitControls } from 'three/examples/jsm/controls/OrbitControls.js';
```
```js
const controls = new OrbitControls( camera, renderer.domElement );
```
Inside animate function:
```js
controls.update();
```
So there you have your 3d scene ready now make changes as you want by taking reference of [three.js documentaion](https://threejs.org/docs/index.html#manual/en/introduction/Creating-a-scene).
