<template>
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
                    
                    <v-container>
                        <v-row>
                        <v-col
                            cols="12"
                            lg="6"
                        >
                            <v-menu
                            ref="menu1"
                            v-model="menu1"
                            :close-on-content-click="false"
                            transition="scale-transition"
                            offset-y
                            max-width="290px"
                            min-width="auto"
                            >
                            <template v-slot:activator="{ on, attrs }">
                                <p>Date in ISO format: <strong>{{ date }}</strong></p>
                                <v-text-field
                                v-model="dateFormatted"
                                label="START"
                                persistent-hint
                                prepend-icon="mdi-calendar"
                                v-bind="attrs"
                                @blur="date = parseDate(dateFormatted)"
                                v-on="on"
                                ></v-text-field>
                            </template>
                            <v-date-picker
                                v-model="date"
                                no-title
                                @input="menu1 = false"
                            ></v-date-picker>
                            </v-menu>

                        </v-col>

                        <v-col
                            cols="12"
                            lg="6"
                        >
                            <v-menu
                            v-model="menu2"
                            :close-on-content-click="false"
                            transition="scale-transition"
                            offset-y
                            max-width="290px"
                            min-width="auto"
                            >
                            <template v-slot:activator="{ on, attrs }">
                                <v-text-field
                                v-model="computedDateFormatted"
                                label="GOAL"
                                persistent-hint
                                prepend-icon="mdi-calendar"
                                readonly
                                v-bind="attrs"
                                v-on="on"
                                ></v-text-field>
                            </template>
                            <v-date-picker
                                v-model="date"
                                no-title
                                @input="menu2 = false"
                            ></v-date-picker>
                            </v-menu>

                        </v-col>
                        </v-row>
                    </v-container>

                </v-card-title>
  
                <v-card-subtitle>
                  スタートの日程とゴールの日程を選択してください
                </v-card-subtitle>
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
  
                    <v-card-subtitle>

                        <v-form v-model="valid">
                            <v-container>
                            <v-row>
                                <v-col
                                cols="25"
                                md="50"
                                >
                                <v-text-field
                                    label="テキスト形式指定"
                                    required
                                ></v-text-field>
                                </v-col>

                                <v-col
                                cols="12"
                                md="4"
                                >
                               
                                </v-col>

                            </v-row>
                            </v-container>
                        </v-form>

                    </v-card-subtitle>
                  </div>
                </div>
              </v-card>
            </v-col>
          </v-row>
        </v-container>
      </v-card>
    </div>
  </template>
  
  <script>
  
  export default {
    name: 'InputArea',

    data: vm => 
        
        ({
            date: (new Date(Date.now() - (new Date()).getTimezoneOffset() * 60000)).toISOString().substr(0, 10),
            dateFormatted: vm.formatDate((new Date(Date.now() - (new Date()).getTimezoneOffset() * 60000)).toISOString().substr(0, 10)),
            menu1: false,
            menu2: false,


            valid: false,
            firstname: '',
            lastname: '',
            nameRules: [
            v => !!v || 'Name is required',
            v => v.length <= 10 || 'Name must be less than 10 characters',
            ],
            email: '',
            emailRules: [
            v => !!v || 'E-mail is required',
            v => /.+@.+/.test(v) || 'E-mail must be valid',
            ],
        }),

        computed: {
            computedDateFormatted () {
            return this.formatDate(this.date)
            },
        },

        watch: {
            date () {
            this.dateFormatted = this.formatDate(this.date)
            },
        },

        methods: {
            formatDate (date) {
            if (!date) return null

            const [year, month, day] = date.split('-')
            return `${month}/${day}/${year}`
            },
            parseDate (date) {
            if (!date) return null

            const [month, day, year] = date.split('/')
            return `${year}-${month.padStart(2, '0')}-${day.padStart(2, '0')}`
            },
        },
    }
  </script>