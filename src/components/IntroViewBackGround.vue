<template>
    <div id="intro-background"
         class="full-screen"
         layout="row center-center">
        <canvas id="background-canvas"
                class="full-screen"
                :style="{background: 'linear-gradient('+
                $store.state.introBgColorFrom+','+$store.state.introBgColorTo+')'}">
        </canvas>
        <slot class="content"
              self="center">
        </slot>
    </div>
</template>

<script>
import {start} from '@/assets/scripts/background.js';

export default {
    mounted() {
        const body = document.querySelector('body');
        start(body);
    },
    name: "HomePageBackGround"
}
</script>

<style lang="less" scoped>
* {
  pointer-events: none;
  user-select: none;
}

#intro-background {
  position: fixed;
  bottom: 0;
}

#background-canvas {
  position: absolute;
  z-index: -1;
}

.content {
  position: absolute;
  z-index: 1;
}
</style>