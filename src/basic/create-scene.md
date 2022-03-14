# Hoạt cảnh
Giả sử chúng ta có 1 đề bài *tạo cảnh 1 mặt trăng quay tròn, đc chiếu sáng ở 1 phía*
Renderer sẽ yêu cầu 2 thứ:
* **Khung cảnh**: bao gồm toàn các đối tượng bên trong (ví dụ theo đề bài: mặt trăng, tia sáng)
* **Camera**: đối tượng quyết định góc nhìn được render.

Thật thú vị khi nó tương tự như bạn đang là đạo diễn của 1 bộ phim vậy,  **Khung cảnh** của bạn là hiện trường với các diễn viên, mọi cảnh vật cây cối. Bạn sẽ cần 1 **Camera** và góc nhìn của camera ghi lại chính là kết quả cuối cùng mà mọi người thấy khi bộ phim hoàn thành. 


## Triển khai
Tạo scene và camera đầu tiên (bạn sẽ vần tạo ra scene và camera trước để cung cấp cho hàm Render của Renderer ở bài trước)

```javascript
// Tạo scene
const scene = new THREE.Scene()

// Tạo camera cơ bản
const camera = new THREE.PerspectiveCamera(75, sizes.width / sizes.height, 0.1, 100)
camera.position.x = 0
camera.position.y = 0
camera.position.z = 2
```


## Reference
Tìm hiểu về các thông số của Camera [Link](https://threejs.org/docs/#api/en/cameras/PerspectiveCamera)