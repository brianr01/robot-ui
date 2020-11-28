<template>
    <div class="text-center" style="background-color:black;">
      <div class="d-flex flex-column">
        <div>
          <h3>Top</h3>
          <img src="http://127.0.0.1:5000/video_feed_1">
        </div>
        <div>
          <h3>Bottom</h3>
          <img src="http://127.0.0.1:5000/video_feed_2">
        </div>
      </div>
      <div class="m-3 d-flex justify-content-center">
        <rubiksCube :cubePosition="cubePosition">
        </rubiksCube>
      </div>
      <div>
        <button
          type="button"
          class="btn btn-danger"
          @click="powerOff()"
        >
          Off
        </button>
        <button
          type="button"
          class="btn btn-success"
          @click="powerOn()"
        >
          On
        </button>
        <button
          type="button"
          class="btn btn-primary"
          @click="turn('r')"
        >
          Right
        </button>
        <button
          type="button"
          class="btn btn-primary"
          @click="turn('l')"
        >
          Left
        </button>
        <button
          type="button"
          class="btn btn-primary"
          @click="turn('u')"
        >
          Up
        </button>
        <button
          type="button"
          class="btn btn-primary"
          @click="turn('d')"
        >
          Down
        </button>
        <button
          type="button"
          class="btn btn-primary"
          @click="turn('f')"
        >
          Front
        </button>
        <button
          type="button"
          class="btn btn-primary"
          @click="turn('b')"
        >
          Back
        </button>
        <button
          type="button"
          class="btn btn-info"
          @click="switch_cameras()"
        >
          Switch
        </button>
        <button
          type="button"
          class="btn btn-warning"
          @click="scramble()"
        >
          Scramble
        </button>
      </div>
    </div>
</template>

<script>
import rubiksCube from '~/components/rubiksCube.vue'
import 'bootstrap/dist/css/bootstrap.css'
import 'bootstrap-vue/dist/bootstrap-vue.css'

export default {
  components: {
    rubiksCube
  },
  data() {
    return {
      test: '',
      cubePosition: {}
    }
  },
  async created() {
    const axios = require('axios');

    this.cubePosition = (await this.$axios.get('/api/get_cube_position')).data
  },
  methods: {
    async powerOff() {
      await this.$axios.get('/api/power?state=False')
    },
    async powerOn() {
      await this.$axios.get('/api/power?state=True')
    },
    async turn(side) {
      await this.$axios.get(`/api/turn?side=${side}&direction=c`)

      this.cubePosition = (await this.$axios.get('/api/get_cube_position')).data
    },
    async switch_cameras() {
      await this.$axios.get(`/api/switch_video_feeds`)
    },
    async scramble() {
      await this.$axios.get(`/api/scramble`)
    }
  }
}
</script>
