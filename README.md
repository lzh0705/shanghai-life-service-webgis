# 上海市生活服务设施查询系统

一个基于高德地图 JavaScript API 2.0 与 ECharts 构建的单页 WebGIS 应用，用于查询、筛选和分析上海市生活服务设施 POI。

## 功能

- 获取并高亮显示上海市行政边界
- 动态查询餐饮、便利店、快递、公共厕所、充电站和地铁站 POI
- 支持关键词、设施类别和模拟运营状态组合筛选
- 支持矩形框选和多边形圈选，并重新查询区域内部 POI
- 展示设施详情、行政区、地址及联系电话
- 通过 KPI、分类占比图和近 7 天趋势图展示区域运营概况
- 支持深色、标准和浅色三种高德底图样式切换
- 支持空结果、接口加载和异常提示

## 技术栈

- HTML5
- CSS3
- JavaScript
- 高德地图 JavaScript API 2.0
- AMap.PlaceSearch
- AMap.DistrictSearch
- AMap.MouseTool
- ECharts 5

## 快速开始

### 1. 获取高德地图凭据

在[高德开放平台](https://console.amap.com/dev/key/app)创建应用，并申请“Web端（JS API）”类型的 Key 与安全密钥。

### 2. 创建本地配置

复制示例配置：

```bash
cp config.example.js config.js
```

Windows PowerShell：

```powershell
Copy-Item config.example.js config.js
```

编辑 `config.js`：

```js
window.AMAP_CONFIG = {
  key: "你的 Web端 Key",
  securityJsCode: "你的安全密钥"
};
```

`config.js` 已加入 `.gitignore`，不会被提交到仓库。请同时在高德控制台配置域名白名单。

### 3. 启动本地服务

推荐通过本地 HTTP 服务打开，不要直接使用 `file://`：

```bash
python -m http.server 8080
```

访问：

```text
http://localhost:8080
```

## 项目结构

```text
.
├── index.html          # 页面、样式与业务逻辑
├── config.example.js   # 高德地图配置模板
├── .gitignore          # 忽略本地凭据
└── README.md           # 项目说明
```

## 数据说明

设施名称、位置、地址、行政区和电话来自高德 PlaceSearch 查询结果。高德 POI 并不统一提供实时营业状态、排队人数或近 7 天客流，因此页面中的“营业中 / 高峰期 / 暂停服务”、拥挤度和趋势数据为稳定生成的演示数据，不代表真实运营情况。

受高德 API 单次查询数量、调用配额及账号权限影响，页面展示的是接口返回的结果集合，并不等同于上海市全部设施总量。

## 安全说明

- 不要将真实 Key 或安全密钥写入 `index.html`
- 不要提交本地 `config.js`
- 为生产 Key 配置域名白名单和调用额度限制
- 如果凭据曾公开提交，请立即在高德控制台更换

## 项目亮点

- 实现上海市域边界、POI 与统计看板的联动展示
- 实现基于用户自定义几何区域的 POI 范围检索
- 将地图交互、数据筛选和 ECharts 图表整合为单页应用
- 使用配置文件隔离本地凭据，便于安全地发布开源代码

## License

本项目仅用于学习与作品集展示。地图与 POI 数据的使用须遵守高德开放平台相关服务条款。
