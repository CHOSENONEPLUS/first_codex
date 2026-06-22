# Qinglu Restaurant Vue

一个使用 Vue 3 和 Vite 构建的餐厅展示页面项目。页面围绕「青炉餐厅」的品牌体验展开，包含首屏介绍、招牌菜单、主厨故事、空间展示和预约表单等模块，适合作为餐饮品牌官网或单页展示站点的基础模板。

## 项目特点

- 基于 Vue 3 Composition API 开发
- 使用 Vite 提供本地开发和构建能力
- 响应式单页布局，适配桌面端和移动端
- 包含导航菜单、滚动页头状态、预约提交反馈等交互
- 使用线上图片资源展示餐厅氛围和菜品内容

## 技术栈

- Vue 3
- Vite
- JavaScript
- CSS

## 本地运行

安装依赖：

```bash
npm install
```

启动开发服务器：

```bash
npm run dev
```

构建生产版本：

```bash
npm run build
```

本地预览构建结果：

```bash
npm run preview
```

## 目录结构

```text
.
├── index.html
├── package.json
├── package-lock.json
├── vite.config.js
└── src
    ├── App.vue
    ├── main.js
    └── style.css
```

## 版本控制说明

项目已通过 `.gitignore` 排除本地依赖、构建产物、日志、环境变量和编辑器配置等文件，例如：

- `node_modules/`
- `dist/`
- `.env`
- `.vscode/`
- 日志和缓存文件
