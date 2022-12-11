<template>
  <v-app>
    
    <v-app-bar color="accent" dark app>
      <v-toolbar-title>Vuetify</v-toolbar-title>
    </v-app-bar>

    <v-content class="my-16">
      <div class="d-flex align-center justify-space-around">
        <div class="flex-column">
          <v-card max-width="400" class="mx-auto" color="#37474F" dark>
            
            <v-data-table
              :headers="headers"
              :items="desserts"
              :items-per-page="5"
              class="elevation-1"
            ></v-data-table>

          </v-card>
          <v-btn color="accent">コピー</v-btn>
        </div> 
        <div>

          <v-card
            max-width="500"
            class="mx-auto"
          >
          <v-container>
              <v-row dense>
                <v-col cols="12">
                  <v-card
                    color="#385F73"
                    dark
                  
                  >
                    <v-card-title class="text-h5" >
                      ○月○日以降〜○月○日まで
                      この時間は×という指定
                      設定をできるようにする
                    </v-card-title>

                    <v-card-subtitle>設定をできるようにする</v-card-subtitle>
                    
                  </v-card>
                </v-col>

                <v-col cols="12">
                  <v-card
                    color="#1F7087"
                    dark
                  >
                    <div class="d-flex flex-no-wrap justify-space-between">
                      <div>
                        <v-card-title class="text-h5">
                          テキスト形式指定
                        </v-card-title>

                        <v-card-subtitle>00:00~00:00スタート〜ゴールみたいな文字</v-card-subtitle>
                      </div>
                    </div>
                  </v-card>
                </v-col>
              </v-row>
            </v-container>
          </v-card>
          <v-btn color="accent">コピー</v-btn>
        </div>
      </div>
    </v-content>

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
  </v-app>
</template>

<script>

  export default {
    data () {
      return {
        icons: [
          'mdi-google',
        ],

        headers: [
          {
            text: '出力',
            align: 'start',
            sortable: false,
            value: 'name',
          },
        ],
        desserts: [
          {
            name: 'Frozen Yogurt',
          },
          {
            name: 'Ice cream sandwich',
          },
          {
            name: 'Eclair',
          },
          {
            name: 'Cupcake',
          },
          {
            name: 'Gingerbread',
          },
          {
            name: 'Jelly bean',
          },
          {
            name: 'Lollipop',
          },
          {
            name: 'Honeycomb',
          },
          {
            name: 'Donut',
          },
          {
            name: 'KitKat',
          },
        ],
      }
    },
  }
</script>