# typewriter-effect-vue

A typewriter effect library for Vue 3, using Vue rendered content.

<img src="https://raw.githubusercontent.com/letrungtan/typewriter-effect-vue/refs/heads/main/src/assets/typewriter-effect-vue.webp" width="650" />

## Installation
### NPM
```js
$ npm i typewriter-effect-vue
```
Use the component.
```js
import { TypewriterEffect } from 'typewriter-effect-vue'
```
## Usage

**Basic Usage**
```html
<TypewriterEffect 
    :active="true"
>
    <div>I<span style='color: #00FFFF;'>'</span>m</div>
    <div>Typewritter Effect for <span style='color: #00FFFF;'>Vue</span></div>
</TypewriterEffect>
```

## Props

| Name                | Type       | Default    | Description                       |
| :------------------ | :--------- | :--------- | :-------------------------------- |
| `id`                | `String`   | ''         | The ID is used when emitting the done event, to identify which element the typing effect is completed for  |
| `active `           | `Boolean`  | null       | Controls whether the typewriter effect is active. If null, the effect will be triggered when mounted  |
| `speed`             | `Number`   | 50         | The speed at which the characters are typed (in milliseconds)  |
| `delay`         | `Number`       | 0          | The delay (in milliseconds) before the typing effect starts  |
| `hideCursorOnDone`  | `Boolean`  | true       |  If set to true, the cursor will be hidden once the typing effect is finished |

## Events

| Event Name     | Args Type       | Description                                           |
|----------------| ---------- | ---------------------------------------------------------- |
| `done`         | `String`   | This event is emitted when the typewriter effect has finished typing all characters. It includes the id of the element as a parameter, which can be used to identify which typing effect has completed.                       |