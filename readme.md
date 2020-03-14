# vue-animation-component

## Setup

via yarn:   

```bash
$ yarn add vue-animate-component
```

via npm:  

```bash
$ npm i --save vue-animate-component
```

## Example

Props are based on [Keyframe Formats](https://developer.mozilla.org/en-US/docs/Web/API/Web_Animations_API/Keyframe_Formats) and [EffectTiming](https://developer.mozilla.org/en-US/docs/Web/API/EffectTiming).  
You can control the start timing of the animation by setting `v-model` attribute.

```html
<template>
  <div id="app">
    <div id="rect">
      <animation v-model="active" :duration="1000" easing="ease">
        <keyframe transform="translate(0, 0)" :offset="0" />
        <keyframe transform="translate(100px, 0)" :offset="0.25" />
        <keyframe transform="translate(50px, 0)" :offset="0.5" />
        <keyframe transform="translate(120px, 0)" :offset="1" />
      </animation>
    </div>
    {{ active ? 'Animating' : 'Stopping' }}
    <button @click="active = !active">Toggle</button>
  </div>
</template>

<script>
import { Animation, Keyframe } from './vue-animation-component/index.js'
export default {
  components: {
    Animation,
    Keyframe
  },
  data() {
    return {
      active: false
    }
  }
}
</script>

<style>
#rect {
  width: 100px;
  height: 100px;
  background-color: red;
}
</style>
```

## Author

shundroid
