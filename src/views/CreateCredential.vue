<template>
  <v-container fluid fill-height>
    <v-row justify="center" align="center">
      <v-card
          class="flex"
          color="transparent"
          flat
          max-width="600"
      >
        <v-card-title class="justify-center">
          <ShowImage :name="nameSet" :url="imgSet"/>
        </v-card-title>
      </v-card>
      <v-card
          color="transparent"
          flat
      >
        <v-card-title>
          <div>
            <v-col>
              <v-row justify="center" class="py-2">
                <v-btn
                    x-large
                    color="red"
                    class="subtitle-1 font-weight-bold white--text"
                    block
                    @click="captureDiv()"
                >DESCARGAR</v-btn>
              </v-row>
              <v-row justify="center" class="py-2">
                <v-btn
                    to="/"
                    x-large
                    block
                    outlined
                    color="red"
                    class="subtitle-1 font-weight-bold"
                >VOLVER</v-btn>
              </v-row>
            </v-col>
          </div>
        </v-card-title>
      </v-card>
      <img :src="output">
    </v-row>
  </v-container>
</template>

<script>
import ShowImage from "@/components/ShowImage";
import html2canvas from 'html2canvas'
export default {
  name: 'CreateCredential',
  components:{
    ShowImage,
  },
  data() {
    return {
      output: null
    }
  },
  computed:{
    nameSet(){
      return this.$route.params.name
    },
    imgSet(){
      return (this.$route.params.url)
    }
  },
  methods: {
    captureDiv(){
      let elem = document.querySelector("#capcred")
      let opts = {
        scrollX: -window.scrollX,
        scrollY: -window.scrollY,
        windowWidth: document.documentElement.offsetWidth,
        windowHeight: document.documentElement.offsetHeight
      }
      html2canvas(elem,opts).then(canvas => {
        const link = document.createElement("a");
        link.setAttribute("download", "d-credencial.jpg");
        link.setAttribute(
            "href",
            canvas.toDataURL("image/jpg").replace("image/jpg", "image/octet-stream")
        );
        link.click();
      });
    },
  }
}
</script>
