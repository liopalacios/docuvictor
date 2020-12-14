<template>
  <v-app :style="{background: $vuetify.theme.themes.light.background}">
      <v-layout row class="justify-center">
          <v-flex md5 center>
              <v-app :style="{background: $vuetify.theme.themes.light.background}">
                  <v-container>
                      <v-flex>
                          <v-card class="ma-2 text-center mt-8" shaped elevation="10">
                                <v-avatar class="mt-n7" size="60" elevation="10">
                                    <!--<img src="../assets/logo.png" alt="">-->
                                    <img src="../assets/logo2.svg" alt="" width="85px"/>
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
                                      <v-autocomplete
                                        v-model="numexpediente"
                                        :items="dataexp"
                                        filled
                                        chips
                                        color="blue-grey lighten-2"
                                        label="Expediente"
                                        item-text="expediente"
                                        item-value="expediente"
                                        
                                        >                                    
                                      </v-autocomplete>
                                      
                                  </v-list-item>
                              </v-list>
                              <v-list subheader="" class="mt-n4">
                                  <v-list-item>
                                      <v-row>
                                          <v-col>
                                              <v-text-field
                                                    v-model="folios"
                                                      label="Cant. Folios"
                                                      outlined
                                              ></v-text-field>
                                          </v-col>
                                          <v-col>
                                            <v-text-field
                                                v-model="avance"
                                                label="Avance %"
                                                outlined
                                            ></v-text-field>
                                          </v-col>
                                      </v-row>


                                  </v-list-item>
                                  <v-list-item>
                                      <v-row>
                                        <v-col>
                                          <v-text-field
                                            v-model="estado"
                                                  label="Estado del proceso"
                                                  outlined
                                          ></v-text-field>
                                        </v-col>
                                        <v-col style="text-align:right">
                                            <img src="../assets/dama.png" alt="" width="125px">
                                        </v-col>
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
        date2: new Date().toISOString().substr(0,10),
        numexpediente: "",
        folios: "",
        avance: 0,
        estado: "",
        dataexp: [
            {expediente:"268-1990",materia:"penal",cantidad:64,porcentaje:"10%",estado:"pendiente"},
            {expediente:"268-1991",materia:"penal",cantidad:150,porcentaje:"3%",estado:"pendiente"},
            {expediente:"268-1992",materia:"penal",cantidad:352,porcentaje:"20%",estado:"pendiente"},
            {expediente:"268-1993",materia:"penal",cantidad:450,porcentaje:"70%",estado:"pendiente"},
            {expediente:"268-1994",materia:"penal",cantidad:451,porcentaje:"20%",estado:"pendiente"},
            {expediente:"268-1995",materia:"penal",cantidad:452,porcentaje:"85%",estado:"pendiente"},
            {expediente:"268-1996",materia:"penal",cantidad:453,porcentaje:"30%",estado:"pendiente"},
            {expediente:"268-1997",materia:"penal",cantidad:504,porcentaje:"20%",estado:"pendiente"},
            {expediente:"268-1998",materia:"penal",cantidad:455,porcentaje:"6%",estado:"pendiente"},
            {expediente:"268-1999",materia:"penal",cantidad:456,porcentaje:"20%",estado:"pendiente"},
            {expediente:"268-2000",materia:"penal",cantidad:250,porcentaje:"40%",estado:"pendiente"},
            {expediente:"268-2001",materia:"penal",cantidad:268,porcentaje:"20%",estado:"pendiente"},
            {expediente:"268-2002",materia:"penal",cantidad:385,porcentaje:"25%",estado:"pendiente"},
            {expediente:"268-2003",materia:"penal",cantidad:698,porcentaje:"20%",estado:"pendiente"},
            {expediente:"268-2004",materia:"penal",cantidad:345,porcentaje:"20%",estado:"pendiente"},
            {expediente:"268-2005",materia:"penal",cantidad:245,porcentaje:"18%",estado:"pendiente"},
            {expediente:"268-2006",materia:"penal",cantidad:184,porcentaje:"20%",estado:"pendiente"},
            {expediente:"268-2007",materia:"penal",cantidad:365,porcentaje:"5%",estado:"pendiente"},
            {expediente:"268-2008",materia:"penal",cantidad:325,porcentaje:"20%",estado:"pendiente"},
            {expediente:"268-2009",materia:"penal",cantidad:365,porcentaje:"4%",estado:"pendiente"},
            {expediente:"268-2010",materia:"penal",cantidad:185,porcentaje:"20%",estado:"pendiente"},
            {expediente:"268-2011",materia:"penal",cantidad:145,porcentaje:"4%",estado:"pendiente"},
        ]
    }),
    computed: {
        theme(){
            return this.$vuetify.theme.dark ? "dark" : "light";
        }
    },
    watch: {      
      numexpediente(val){
          if(val.length > 0){
              var exp = this.dataexp.filter(datae => datae.expediente==val)
              this.folios = exp[0].cantidad
              this.avance = exp[0].porcentaje
              this.estado = exp[0].estado
              console.log(this.folios)
          }
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
