# Khởi động
Chúng ta sẽ bắt đầu với việc setup ThreeJS , take note lại các khái niệm cơ bản nhất
## Cài đặt ThreeJs

```javascript
npm install --save three
// Import thư viện
import * as THREE from 'three';
```

## Triển khai
> ThreeJS sẽ render hoạt cảnh của nó trên canvas, bởi vậy hiệu suất đem lại sẽ cực kỳ tốt. Chúng ta có thể style css với canvas chỉ định, thường các hoạt cảnh sẽ được dùng để làm backgound cho landing page hoặc đôi khi tất cả website đều được dựng bởi canvas


1. Khởi tạo 1 canvas, khởi tạo **Renderer** phụ trách việc render và thiết lập các thông số

```html
<canvas class="webgl"></canvas>
<style>
    .webgl{
        position: fixed;
        top: 0;
        left: 0;
        outline: none;
    }
</style>
```

Import thư viện threejs và cấu hình
```javascript
import * as THREE from 'three';
// 1.Lấy đối tượng dom canvas
const canvas = document.querySelector('canvas.webgl')

// 2. Tạo đối tương renderer phụ trách viêc render
// @canvas: canvas sẽ render
// @alpha: chế độ nền có trong suốt hay không
const renderer = new THREE.WebGLRenderer({
    canvas: canvas,
    alpha: true 
})
// thiết lập kích thước và tỉ lệ pixel, ở đây mình dùng full window luôn
renderer.setSize(window.innerWidth, window.innerHeight) 
renderer.setPixelRatio(Math.min(window.devicePixelRatio, 2))

```

2. Sau khi đã có renderer, chúng ta cần truyền vào hoạt cảnh để renderer thực hiện công việc render của nó.

> Vì bản chất của việc render ra hoạt cảnh thực chất là render rất nhiều các khung hình (tương tự như frame khi xây dựng video) nên bản chất chúng ta cần 1 function gọi đệ quy việc render để sinh ra chuyển động *window.requestAnimationFrame(tick)*
Đó là lý dó chúng ta cần function Tick()

```javascript
const tick = () =>
{
    // Các đoạn code điều chỉnh thông số tại đây sẽ quyết định animation


    // 1. Sử dụng đối tượng renderer để bắt đầu render (scene, camera)
    // 2. Gọi requestAnimationFrame chạy lại hàm tick() cho lượt render tiếp theo
    renderer.render(scene, camera) 
    window.requestAnimationFrame(tick)
}
tick()
```

3. Vậy là phần thiết lập chính đã xong, tiếp tục với với việc tạo hoạt cảnh


## Reference
* Chi tiết cài đặt [Link](https://threejs.org/docs/#manual/en/introduction/Installation)
