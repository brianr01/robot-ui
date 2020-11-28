<template>
  <div class="cube">
    <div class="cube-row d-flex justify-content-center">
      <div class="face d-flex flex-row flex-wrap">
        <div v-for="(sticker, index) in cubePosition.u" :key="index" class="sticker border border-dark">
          <div :style="'background-color:' + colorMap[sticker[0]]" class="w-100 h-100">
          </div>
        </div>
      </div>
    </div>
    <div class="cube-row d-flex flex-row">
      <div class="face d-flex flex-row flex-wrap">
        <div v-for="(sticker, index) in cubePosition.l" :key="index" class="sticker border border-dark">
          <div :style="'background-color:' + colorMap[sticker[0]]" class="w-100 h-100">
          </div>
        </div>
      </div>
      <div class="face d-flex flex-row flex-wrap">
        <div v-for="(sticker, index) in cubePosition.f" :key="index" class="sticker border border-dark">
          <div :style="'background-color:' + colorMap[sticker[0]]" class="w-100 h-100">
          </div>
        </div>
      </div>
      <div class="face d-flex flex-row flex-wrap">
        <div v-for="(sticker, index) in cubePosition.r" :key="index" class="sticker border border-dark">
          <div :style="'background-color:' + colorMap[sticker[0]]" class="w-100 h-100">
          </div>
        </div>
      </div>
    </div>
    <div class="cube-row d-flex justify-content-center">
      <div class="face d-flex flex-row flex-wrap">
        <div v-for="(sticker, index) in cubePosition.d" :key="index" class="sticker border border-dark">
          <div :style="'background-color:' + colorMap[sticker[0]]" class="w-100 h-100">
          </div>
        </div>
      </div>
    </div>
    <div class="cube-row d-flex justify-content-center">
      <div class="face d-flex flex-row-reverse flex-wrap-reverse">
        <div v-for="(sticker, index) in cubePosition.b" :key="index" class="sticker border border-dark">
          <div :style="'background-color:' + colorMap[sticker[0]]" class="w-100 h-100">
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      colorMap: {
        u: 'white',
        d: 'yellow',
        r: 'red',
        l: 'orange',
        f: 'green',
        b: 'blue'
      },
    }
  },
  props: {
    cubePosition: Object
  }
}
</script>

<style scoped>
.cube {
  width: 540px;
}
.face {
  width: 180px;
  height: 180px;
  display: inline-block;
}
.sticker {
  width: 60px;
  height: 60px;
}
</style>