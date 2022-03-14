> Giả sử chúng ta có 1 đề bài *tạo cảnh 1 mặt trăng quay tròn, đc chiếu sáng ở 1 phía*
# Scene
Một scene sẽ cho phép thêm các đối tượng với function **add**. Bạn sẽ tạo các đối tượng, ví dụ ở đấy là 1 mặt trăng (moon), sau đó dùng **scene.add(moon)**

## 1. Đối tượng Mesh - Mặt trăng
1. Các khái niệm
Đối tượng Mặt trăng chúng ta tạo ra trong thế giới Threejs được coi là 1 **Mesh**. Đây là một vật thể 3D, nó được cấu thành từ **Geometry** và **Material**
* **Geometry**: là khung xương của vật thể, xác định hình dạng hình học của vật thể
* **Material**: là vỏ bọc, xác định bề ngoài của vật thể

2. Triển khai
```javascript

// Tạo Geometry cho mặt trăng 
// SphereBufferGeometry tạo khối cầu
const moonGeometry = new THREE.SphereBufferGeometry(.9, 64, 64)

// Tạo Material cho mặt trăng - Thiết lập màu trắng bao phủ
const moonMaterial = new THREE.MeshStandardMaterial()
moonMaterial.color = new THREE.Color(0xffffff)

// Mesh
const moon = new THREE.Mesh(moonGeometry,moonMaterial)
scene.add(moon)
```

### 1.2 Geometry - Cấu trúc hình học
ThreeJS cung cấp các thư viện tạo khung hình cơ bản, tạo khối cầu *(SphereBufferGeometry)*, khối vuông  *(BoxGeometry)*, ..v.v.
* Khối cơ bản [Tài liệu các khối](https://threejs.org/docs/#api/en/geometries/BoxGeometry)
* Tuy nhiên trong thực tế, chúng ta sẽ có các hình khối phức tạp hơn, tạo ra từ các phần mềm 3D chẳng hạn, mình gọi đó là các **Custom Geometry**, sẽ tìm hiểu sau*

### 1.2 Material - Bề mặt
MeshStandardMaterial để khởi tạo bề mặt cơ bản, nó sẽ cung cấp các thuộc tính như màu sắc, độ trong suốt, ..v..v.
* Thông số cấu hình [Tài liệu Material](https://threejs.org/docs/#api/en/materials/MeshStandardMaterial)
* normalMap: đây là thông số cho phép bạn đưa vào texture để apply lên bề mặt.(ví dụ bề mặt lồi lõm của mặt trăng)
**Texture** có thể là 1 file ảnh bề mặt, bạn có thể search key word **normal map** hoặc **texture**
#### Triển khai Texture
1. Cung cấp file texture của bạn, có thể sử dụng [Tool normalMap Generate](https://cpetry.github.io/NormalMap-Online/)
2. Load texture từ folder chỉ định và cầu hình normal map

```javascript
// Load texture với TextureLoader, quá trình này take time nên đó là lý do vì sao các web 3d hay tạo loading
const textureLoader = new THREE.TextureLoader();
const myMoonTexture = textureLoader.load('/textures/normalMap.png')

const moonMaterial = new THREE.MeshStandardMaterial()
moonMaterial.normalMap = myMoonTexture;
```


## 2. Ánh sáng
Nếu bạn đã thực hiện việc thêm 1 mặt trăng, nhưng khi render lại chỉ thấy một màu đen thui !!! Đó là lúc bạn cần tới **Ánh sáng - light** .
Scene đã được dựng, mặt trăng đã đc tạo nhưng khung cảnh ban đầu chưa có ánh sáng nên bạn sẽ không thể nhìn thấy vật thể bạn tạo ra. Bởi vậy bạn cần tạo 1 nguồn chiếu sáng - (giống như mặt trời hoặc đèn pin vậy) và add vào scene

Triển khai **PointLight**
```javascript
// Khởi tạo ánh sáng chiếu - với cấu hình màu sắc nguồn sáng, độ rộng, vị trí
const pointLight = new THREE.PointLight(0xffffff, 0.2)
pointLight.position.x = -1.63
pointLight.position.y = 0.97
pointLight.position.z = 0.7
scene.add(pointLight)


// Sử dụng PointLightHelper để hiện vị trí nguồn sáng phục vụ việc debug
const lightHelper = new THREE.PointLightHelper(pointLight, .6);
scene.add(lightHelper)
```

**PointLight** chỉ là một dạng ánh sáng cơ bản mà ThreeJS cung cấp [Tài liệu light](https://threejs.org/docs/#api/en/lights/PointLight)