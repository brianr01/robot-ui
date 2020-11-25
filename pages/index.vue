<template>
  <v-app>
    <div class="text-center">
      <v-btn
        class="ma-2"
        color="error"
        @click="powerOff()"
      >
        Off
      </v-btn>
      <v-btn
        class="ma-2"
        color="success"
        @click="powerOn()"
      >
        On
      </v-btn>
      <v-btn
        class="ma-2"
        color="primary"
        @click="turn('r')"
      >
        Right
      </v-btn>
      <v-btn
        class="ma-2"
        color="primary"
        @click="turn('l')"
      >
        Left
      </v-btn>
      <v-btn
        class="ma-2"
        color="primary"
        @click="turn('u')"
      >
        Up
      </v-btn>
      <v-btn
        class="ma-2"
        color="primary"
        @click="turn('d')"
      >
        Down
      </v-btn>
      <v-btn
        class="ma-2"
        color="primary"
        @click="turn('f')"
      >
        Front
      </v-btn>
      <v-btn
        class="ma-2"
        color="primary"
        @click="turn('b')"
      >
        Back
      </v-btn>
      <v-btn
        class="ma-2"
        color="primary"
        @click="switch_cameras()"
      >
        Switch
      </v-btn>
      <v-btn
        class="ma-2"
        color="primary"
        @click="scramble()"
      >
        Scramble
      </v-btn>
      <div style="float:left"  width="40%">
        <h3>Top</h3>
        <img src="http://127.0.0.1:5000/video_feed_1">
      </div>
      <div style="float:right" width="40%">
        <h3>Bottom</h3>
        <img src="http://127.0.0.1:5000/video_feed_2">
      </div>
    </div>
  </v-app>
</template>

<script>
import Logo from '~/components/Logo.vue'
import VuetifyLogo from '~/components/VuetifyLogo.vue'

export default {
  components: {
    Logo,
    VuetifyLogo
  },
  data() {
    return {
      test: '',
    }
  },
  async created() {
    const axios = require('axios');

    console.log(this.test)
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
