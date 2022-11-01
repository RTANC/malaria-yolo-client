<template>
  <v-app>
    <v-app-bar app color="green darken-4" dark>
      <v-app-bar-title>
        <h3 class="text-uppercase">Malaria diagnosis automatic system</h3>
      </v-app-bar-title>
    </v-app-bar>
    <v-main style="background-color: #2E7D32;">
      <v-container grid-list-md fluid>
        <v-layout row wrap>
          <v-flex xs6>
            <v-card>
              <v-card-text>
                <v-file-input name="file" accept="image/png, image/jpeg" label="UPLOAD" truncate-length="15" color="green darken-4" show-size
                  prepend-icon="mdi-image" light @change="handleUpload"></v-file-input>
              </v-card-text>
            </v-card>
          </v-flex>
          <v-flex xs6>
            <v-card>
              <v-card-text>
                <v-btn color="primary" @click="diagnosis">text</v-btn>
              </v-card-text>
            </v-card>
          </v-flex>
          <v-flex xs12>
            <v-card>
              <v-card-text>
                <img id="preview" style="width: 100%;"/>
              </v-card-text>
            </v-card>
          </v-flex>
          <v-flex xs12>
            <v-card>
              <v-card-text>
                <canvas id="myCanvas" style="width: 100%;"></canvas>
              </v-card-text>
            </v-card>
          </v-flex>
        </v-layout>
      </v-container>
      <!-- <router-view /> -->
    </v-main>
  </v-app>
</template>

<script>

export default {
  name: 'App',
  data: () => ({
    img: ''
  }),
  methods: {
    handleUpload (file) {
      if (file) {
        const prev = document.getElementById('preview')
        const reader = new FileReader()

        reader.addEventListener('load', function () {
          // console.log(this.result)
          prev.setAttribute('src', this.result)
        })
        reader.readAsDataURL(file)
      }
    },
    diagnosis () {
      var canvas = document.getElementById('myCanvas')
      var context = canvas.getContext('2d')
      var img = document.getElementById('preview')
      context.drawImage(img, 0, 0, 700, 700)
    }
  }
}
</script>
