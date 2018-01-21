## Helloworld
### 说明
- scene 是一个容器，用来保存并跟踪渲染的物体
- camera 定义了 能在渲染好的scene中看到什么，即哪些东西可以被渲染

### 扩展
`渲染器` Render
除了基于 WebGL 的渲染器外，还有其他渲染器。如基于画板(Canvas)的渲染器，基于 SVG 的渲染器。尽管他们可以工作也可以渲染简单的场景，但是不建议使用，因为他们十分`耗费CPU资源`，也`缺乏某些功能`，如支持复杂材质和阴影。

### 步骤
- 新建 场景 
  - 新建 `坐标系` 添加到场景中
  - 新建 `几何体` 添加到场景中
- 新建 透视相机 设置相机位置 & 拍摄角度
- 新建 渲染器 设置渲染器颜色 & 尺寸 
- 将渲染器的domElement绑定到真实的dom元素中
- 渲染

### 灯光
- 新建 灯光 设置灯光位置 & 添加到场景中
- 材质分为 光敏感型(MeshBasicMaterial) 和 光不敏感型(MeshLambertMaterial、MeshPhongMaterial),后者不会对光源产生反应

  
### 投影
`渲染阴影会花费大量的计算资源`，默认threejs不会开启。使用阴影步骤：
- 将render的 `shadowMapEnabled` 设置为 true
- 将需要用投影的 `几何体`的相应属性设置为 true（plane的 receiveShadow属性、其他立体的 castShadow属性）
- 将需要启用投影的`光源`的castShadow属性设置为true

### 动画
setInterval存在的问题
- 不考虑浏览器中发生的事情独立运行，如浏览其他页面或者进入别的Tab时仍会运行
- setInterval 没有跟显示器的重画同步
- 导致较高的CPU使用率，降低系统效率


### 常用库
dat.gui.js(By Threejs 作者)调整动画效果的GUI控件
stats.js 监测动画运行的帧频