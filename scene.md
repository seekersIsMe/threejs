> 它是在渲染时你想使用的所有物体、光源的容器
## `Scene`基础方法
1. `THREE.Scene.add`向场景中加对象
2. `THREE.Scene.remove`移除场景中的对象
3. `THREE.Scene.children`返回场景中的子对象
4. `THREE.Scene.getObjectByName`通过对象的name属性获取该对象
5. `THREE.Scene.traverse`接受一个回调函数，场景中的每个对象都会调用

## `Scene`雾化`fog`
> 场景中的物体离摄像机越远就会变得越模糊
    ```
    scene.fog= new THREE.Fog(0xffffff, 0.01, 100)
    // 0.01表示近处的属性值
    // 100表示远处的属性值
    // 通过这两个属性可以决定雾化开始和结束的地方，以及加深的程度,并且雾的浓度是线性增长的
    ```

## `Scene`材质覆盖`overrideMaterial`
> 场景中的所有的物体都采用`overrideMaterial`定义的材质，即使物体定义了自己的材质，当场景中所有的物体都公用一个材质，可以使用该属性减少threejs管理材质数量来提升性能
    ```
        scene.overrideMaterial = new THREE.MeshLambertMaterial({
            color: 0xAAAAAA
        })
    ```