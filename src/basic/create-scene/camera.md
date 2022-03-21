# Camera
Camera là đối tượng cũng cấp góc nhìn chơ Scene của bạn. Góc nhìn của camera tương tự như chiếc máy chiếu.
ThreeJS cũng cấp 2 loại camera là 
* **OrthographicCamera** : Đây là loại camera thường dùng để chiếu hoạt cảnh 2D.
* **PerspectiveCamera**: Đây là loại chính chúng ta sẽ dùng vì nó cung cấp góc nhìn như cách chúng ta nhìn qua đôi mắt thực tế. Cũng là camera phổ biến để làm việc với các hoạt cảnh 3D

##Triển khai 

```javascript
import { PerspectiveCamera } from 'three';

const fov = 35; // AKA Độ rộng khung cảnh
const aspect = container.clientWidth / container.clientHeight; // tỉ lệ container
const near = 0.1; // khoảng tiêu cự gần nhất
const far = 100; // khoảng tiêu cự xa nhất

const camera = new PerspectiveCamera(fov, aspect, near, far);
camera.postion.set(0, 0 ,5)
```

* Thường các object khi tạo ra sẽ nằm ở vị trí x:0, y:0, z:0. Đối tượng camera mặc định cũng có vị trí như vậy, bở vậy bạn cần đăt camera lùi ra phía trước 1 khoảng để có thể quan sát đối tượng . (ví dụ: x: 0, y: 0, z: 5)
* Đừng quên add camera vào renderer nhé