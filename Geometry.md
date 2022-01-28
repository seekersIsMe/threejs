## 通过定义立方体定点，构建立方体
> **三角面的顶点顺序如果是顺时针，则是面向相机，逆时针则是背向相机，注意这个顺时针还是逆时针判断是将自己置身立方体内部的顺序**
```
    // 定义正方体的八个定点
            var vertices = [
        new THREE.Vector3(2, 2, 2),
        new THREE.Vector3(2, 2, 0),
        new THREE.Vector3(2, 0, 2),
        new THREE.Vector3(2, 0, 0),
        new THREE.Vector3(0, 2, 0),
        new THREE.Vector3(0, 2, 2),
        new THREE.Vector3(0, 0, 0),
        new THREE.Vector3(0, 0, 2)
    ];
    // 
    var faces = [
        new THREE.Face3(0, 2, 3),
        new THREE.Face3(0, 3, 1),
        new THREE.Face3(4, 6, 5),
        new THREE.Face3(6, 7, 5),
        new THREE.Face3(4, 5, 1),
        new THREE.Face3(5, 0, 1),
        new THREE.Face3(7, 6, 2),
        new THREE.Face3(6, 3, 2),
        new THREE.Face3(5, 7, 0),
        new THREE.Face3(7, 2, 0),
        new THREE.Face3(1, 3, 4),
        new THREE.Face3(3, 6, 4),
    ];
        let geo = new THREE.Geometry()
        geo.vertices = vertices
        geo.faces = faces
        geo.computeFaceNormals()
        let geoMaterial = new THREE.MeshLambertMaterial({ // MeshLambertMaterial材质会对光源有反应，基础材质对光源没有反应，这里使用点光源
            color: 0xAA0000,
            opacity: 0.3,
            transparent: true // 是否透明
        })
        // 增加三角面辅助线
        let wireframe = new THREE.WireframeGeometry(geo)
        let line = new THREE.LineSegments(wireframe)
        line.material.linewidth = 2
        scene.add(line)
```