<template>
  <v-app :style="{background: $vuetify.theme.themes.light.background}">
      <v-layout row class="justify-center">
          <v-flex md5 center>
              <v-app :style="{background: $vuetify.theme.themes.light.background}">
                  <v-container>
                      <v-flex>
                          <v-card class="ma-2 text-center mt-8" shaped elevation="10">
                                <v-avatar class="mt-n7" size="60" elevation="10">
                                    <img src="../assets/logo.png" alt="">
                                </v-avatar>
                                <v-card-title class="layout justify-center">El CODEX</v-card-title>
                                <v-card-subtitle class="layout justify-center">Tramitación</v-card-subtitle>
                          </v-card>
                      </v-flex>
                      <v-flex>
                          <v-card class="ma-2 mt-6" elevation="10">
                              <v-list>
                                  <v-list-item>
                                      <v-list-item-avatar size="10" color="cyan darken-1"></v-list-item-avatar>
                                      <v-list-item-title class="nl-n2">Formulario</v-list-item-title>
                                      <v-list-item-subtitle></v-list-item-subtitle>
                                  </v-list-item>

                                  <v-divider></v-divider>
                              </v-list>
                              <v-list two-line="" subheader="">
                                  <v-list-item>
                                      <v-text-field
                                              label="N° Expediente"
                                              outlined
                                      ></v-text-field>
                                      <v-text-field
                                              label="Avance %"
                                              outlined
                                      ></v-text-field>
                                  </v-list-item>
                              </v-list>
                              <v-list subheader="" class="mt-n4">
                                  <v-list-item>
                                      <v-row>
                                          <v-col>
                                              <v-text-field
                                                      label="Cant. Folios"
                                                      outlined
                                              ></v-text-field>
                                          </v-col>
                                          <v-col>

                                          </v-col>
                                      </v-row>


                                  </v-list-item>
                                  <v-list-item>
                                      <v-row>
                                        <v-col>
                                          <v-text-field
                                                  label="Estado del proceso"
                                                  outlined
                                          ></v-text-field>
                                        </v-col>
                                        <v-col></v-col>
                                      </v-row>

                                  </v-list-item>
                              </v-list>
                          </v-card>
                      </v-flex>
                  </v-container>
              </v-app>
          </v-flex>
      </v-layout>
  </v-app>
</template>

<script>
const gradients = [
    ['#222'],
    ['#42b3f4'],
    ['red','orange','yellow'],
    ['purple','violet'],
    ['#00c6ff','#F0F','#FF0'],
    ['#f72044','#ffd200','#1feaea'],
]
export default {
    data: () => ({
        with: 2,
        radius: 10,
        padding: 8,
        lineCap: "round",
        gradient: gradients[5],
        value: [0,2,5,9,5,10,3,5,0,0,1,8,2,9,0],
        gradientDirection: 'top',
        gradients,
        fill: false,
        type: 'trend',
        autoLineWidth: false,
        arrayEvents: null,
        date2: new Date().toISOString().substr(0,10)
    }),
    computed: {
        theme(){
            return this.$vuetify.theme.dark ? "dark" : "light";
        }
    },
    mounted() {
        this.arrayEvents = [...Array(6).map(()=> {
            const  day = Math.floor(Math.random()*30)
            const d = new Date()
            d.setDate(day)
            return d.toISOString().substr(0,10)
        }
        )]
    },
    methods: {
        functionEvents(date) {
            const [,,day] = date.split('-')
            if([12,17,28].includes(parseInt(day,10))) return true
            if([1,19,22].includes(parseInt(day,10))) return ['red','#00f']
            return false
        }
    }

}
</script>

<style scoped>
.rounded {
    border-top-left-radius: 50px;
    border-bottom-left-radius: 50px;
}
</style>
