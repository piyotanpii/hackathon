<template>
	<v-footer
      dark
      padless
    >
      <v-card
        flat
        tile
        class="accent white--text text-center"
        color="#00B0FF"
      >
        <v-card-text>
          <v-btn
            v-for="icon in icons"
            :key="icon"
            class="mx-4 white--text"
            icon
          >
            <v-icon size="30px">
              {{ icon }}
            </v-icon>
            
          </v-btn>
        </v-card-text>

        <v-card-subtitle class="white--text pt-0">
          ---------------------------------------------------Connect with your Google Calendar!
          By linking to Google, it will be possible to retrieve available time outside of the specified time.
          Make scheduling easier.------------------------------------------------------------
        </v-card-subtitle>
      </v-card>
    </v-footer>
</template>

<script>
export default {
	name: 'FooterArea',
    data () {
        return {
            icons: [
            'mdi-google',
            ]}
    }
}


</script>

<style scoped>

</style>