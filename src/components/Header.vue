<template>
  <v-card
      color="transparent"
      flat
      :height="$vuetify.breakpoint.xs ? '100px' : '200px'"
      tile
  >
    <v-toolbar
        dark
        color="transparent"
        flat
        prominent
    >
      <v-img
          :src="require('@/assets/CCAT-LogoBlanco.png')"
          :max-height="$vuetify.breakpoint.xs ? 70 : 90"
          :max-width="$vuetify.breakpoint.xs ? 70 : 90"
          contain
      ></v-img>

      <v-spacer></v-spacer>

      <span
          class="text-center text-h4 pt-10"
          :class="$vuetify.breakpoint.xs ? 'text-subtitle-2' : 'text-h4'"
      >"PANEL DE ESPECIALISTAS CON MIRA AL BICENTENARIO"</span>

      <v-spacer></v-spacer>

    </v-toolbar>
  </v-card>
</template>

<script>
export default {
  name: "Header"
}
</script>
