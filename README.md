# vue-chart-doughnut

Simple doughnut chart for vue.js 3

### Demo

[Codesandbox](https://codesandbox.io/s/vue-chart-doughnut-d668sx)

![doughnut chart preview](./src/assets/img/for-readme/01.png)

## Installation and Usage
```sh
npm i vue-chart-doughnut
```
#### Import into a single component.
```js
import ChartDoughnut from 'vue-chart-doughnut';
```
```vue
<template>
	<chart-doughnut per="5" color="#C3AED6" color-bg="#CDC9C3" text-size="40" />
	<chart-doughnut per="85" />
	<chart-doughnut per="100" />
</template>
```

## Project Setup

```sh
npm install
```

### Compile and Hot-Reload for Development

```sh
npm run dev
```

### Compile and Minify for Production

```sh
npm run build
```
