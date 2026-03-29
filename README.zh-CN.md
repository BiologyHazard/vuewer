# Vuewer

[![npm version](https://img.shields.io/npm/v/vuewer.svg)](https://www.npmjs.com/package/vuewer)
[![npm downloads](https://img.shields.io/npm/dm/vuewer.svg)](https://www.npmjs.com/package/vuewer)
[![license](https://img.shields.io/github/license/BiologyHazard/vuewer.svg)](https://github.com/BiologyHazard/vuewer/blob/main/LICENSE)

[English](./README.md) | **简体中文**

Vuewer 是一个专为 [**Vue 3**](https://vuejs.org/) 打造的图片预览组件，基于 [**Nuxt UI**](https://ui.nuxt.com/)、[**Tailwind CSS**](https://tailwindcss.com/)、[**VueUse**](https://vueuse.org/) 等现代技术栈，拥有美观的界面和极致的交互体验。

## 主要特性

- 🎨 **界面现代**：由 [Nuxt UI](https://ui.nuxt.com/) 和 [Tailwind CSS](https://tailwindcss.com/) 驱动，支持暗色/亮色模式，细节精致，风格统一。
- 🧰 **功能丰富**：支持图片下载、新标签页打开、缩放、旋转、拖拽、背景颜色切换等多种操作。
- ⌨️ **快捷键全覆盖**：所有操作均有快捷键，支持 WASD、方向键、数字键、R、0、1~9、-、= 等快捷键。
- 🤝 **用户友好**：内置帮助菜单，所有功能和快捷键一目了然，上手零门槛。
- 🚀 **动画丝滑**：使用自己编写的 `useAnimateWhenever` 组合式函数，带来流畅的动画和交互体验。
- 🪄 **集成简单**：导入组件即可用，无需复杂配置。
- 🛠️ **开发友好**：TypeScript 类型支持，源码开放，便于二次开发。

## 安装方法

```bash
npm install vuewer
# 或者
yarn add vuewer
# 或者
pnpm add vuewer
# 或者
bun add vuewer
```

### 依赖说明

请确保你的项目已安装以下依赖：

```bash
npm install @nuxt/ui tailwindcss @vueuse/core vue
# 或者
yarn add @nuxt/ui tailwindcss @vueuse/core vue
# 或者
pnpm add @nuxt/ui tailwindcss @vueuse/core vue
# 或者
bun add @nuxt/ui tailwindcss @vueuse/core vue
```

## 快速上手

### 1. 配置 Tailwind CSS

在你的主 CSS 文件（如 `src/assets/main.css`）中添加：

```css
/* src/assets/main.css */

@import 'tailwindcss';
@import '@nuxt/ui';

/* 添加这一行以扫描 vuewer 的源代码 */
@source '../../node_modules/vuewer/src/**/*.{vue,js,ts}';

/* 其他样式... */
```

### 2. 组件用法示例

```vue
<script setup lang="ts">
import { ref } from 'vue'
// Import components from the vuewer package
import { AppImagePreview, ImagePreviewContainer } from 'vuewer'

const previewRef = ref()

const handleOpen = () => {
  previewRef.value?.open({
    url: 'https://picsum.photos/512/512',
    name: 'Example',
    downloadName: 'example.jpg'
  })
}
</script>

<template>
  <div>
    <ImagePreviewContainer @click="handleOpen">
      <img src="https://picsum.photos/512/512" alt="Preview" />
    </ImagePreviewContainer>

    <AppImagePreview ref="previewRef" />
  </div>
</template>
```

## 组件 API

### `AppImagePreview`

- **方法**：
  - `open(target: PreviewTarget)` 打开图片预览弹窗

### `ImagePreviewContainer`

- 提供悬浮特效和放大镜图标的包裹组件
