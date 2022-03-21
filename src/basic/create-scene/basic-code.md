# Full code
Tạo cảnh 1 mặt trăng quay tròn, đc chiếu sáng ở 1 phía

Đoạn code dưới sẽ render 1 khung hình , không chuyển động, 
```html
 <div id="scene-container">
 </div>
```

```javascript
import {
  BoxBufferGeometry,
  Color,
  Mesh,
  MeshBasicMaterial,
  PerspectiveCamera,
  Scene,
  WebGLRenderer,
} from 'three';

//Container
const container = document.querySelector('#scene-container');

// Scene
const scene = new THREE.Scene()

// Camera
const camera = new THREE.PerspectiveCamera(75, sizes.width / sizes.height, 0.1, 100)
camera.position.set(0,0,2)

// Geometry
const moonGeometry = new THREE.SphereBufferGeometry(.9, 64, 64)

// Materials
const moonMaterial = new THREE.MeshStandardMaterial()
material.color = new THREE.Color(0xffffff)

// Mesh
const sphere = new THREE.Mesh(moonGeometry,moonMaterial)
scene.add(sphere)

// Create pointLight
const pointLight = new THREE.PointLight(0xffffff, 0.2)
pointLight.position.set( -1.63, 0.97, 0.7 )
pointLight.intensity = .6;
scene.add(pointLight)

// create the renderer
const renderer = new WebGLRenderer();
renderer.setSize(container.clientWidth, container.clientHeight); //  same size as our container element
renderer.setPixelRatio(window.devicePixelRatio); //  scene will look good on HiDPI displays
container.append(renderer.domElement);

// Start render a frame
renderer.render(scene, camera);
```

Function đệ quy tạo chuyển động quay tròn
``` javascript
// Tạo function tick đệ quy tạo animation
const tick = () =>
{
    const elapsedTime = clock.getElapsedTime()

    // Update objects
    moonGeometry.y = .5 * elapsedTime


    // Render
    renderer.render(scene, camera)
    // Call tick again on the next frame
    window.requestAnimationFrame(tick)
}
tick()
```