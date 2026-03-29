# Vuewer

[![npm version](https://img.shields.io/npm/v/vuewer.svg)](https://www.npmjs.com/package/vuewer)
[![npm downloads](https://img.shields.io/npm/dm/vuewer.svg)](https://www.npmjs.com/package/vuewer)
[![license](https://img.shields.io/github/license/BiologyHazard/vuewer.svg)](https://github.com/BiologyHazard/vuewer/blob/main/LICENSE)

**English** | [简体中文](./README.zh-CN.md)

A refined image preview component for [**Vue 3**](https://vuejs.org/), powered by [**Nuxt UI**](https://ui.nuxt.com/), [**Tailwind CSS**](https://tailwindcss.com/), and [**VueUse**](https://vueuse.org/).

## Features

- 🎨 **Stunning Interface**: Modern, elegant UI powered by [Nuxt UI](https://ui.nuxt.com/) and [Tailwind CSS](https://tailwindcss.com/), with seamless dark/light mode and refined details.
- 🧰 **Comprehensive Features**: Download images, open in new tab, zoom, rotate, drag, change background, and more—everything you expect from a professional image viewer.
- ⌨️ **Powerful Shortcuts**: Every action is accessible via intuitive keyboard shortcuts (WASD, arrow keys, R, 0, 1~9, -, =, and more) for maximum efficiency.
- 🤝 **User Friendly**: Built-in help menu with clear instructions and shortcut references—no learning curve, just productivity.
- 🚀 **Silky Animations**: Ultra-smooth transitions and interactions, powered by the custom `useAnimateWhenever` composable.
- 🪄 **Effortless Integration**: Import and use instantly—no complex setup required.
- 🛠️ **Developer Oriented**: Full TypeScript support, and open-source codebase for easy customization and extension.

## Installation

```bash
npm install vuewer
# or
yarn add vuewer
# or
pnpm add vuewer
# or
bun add vuewer
```

### Peer Dependencies

Ensure you have the following packages installed in your project:

```bash
npm install @nuxt/ui tailwindcss @vueuse/core vue
# or
yarn add @nuxt/ui tailwindcss @vueuse/core vue
# or
pnpm add @nuxt/ui tailwindcss @vueuse/core vue
# or
bun add @nuxt/ui tailwindcss @vueuse/core vue
```

## Setup

### 1. Tailwind CSS Configuration

Since this package distributes **Source Code**, you need to tell Tailwind to scan the package files in your main CSS file (e.g., `src/assets/main.css`):

```css
/* src/assets/main.css */

@import 'tailwindcss';
@import '@nuxt/ui';

/* Add this line to scan vuewer source code */
@source '../../node_modules/vuewer/src/**/*.{vue,js,ts}';

/* Your custom styles... */
```

### 2. Usage

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

## Component API

### `AppImagePreview`

- **Exposed Methods**:
  - `open(target: PreviewTarget)`: Open the preview overlay.

### `ImagePreviewContainer`

- A wrapper component that provides hover effects and a zoom-in icon.
