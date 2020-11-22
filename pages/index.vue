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
      <img src="http://127.0.0.1:5000/video_feed_1" width="40%" style="float:right">
      <img src="http://127.0.0.1:5000/video_feed_2" width="40%" style="float:left">
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
    }
  }
}
</script>
