<template>
  <v-layout
    column
    justify-center
    align-center
  >
    <v-flex
      xs12
      sm8
      md6
    >
        <v-row><v-col>
          <v-card
            class="mx-auto"
            cols="8"
          >
            <v-card-text align="center">
              <div class="display-2 text--primary">{{ year }}年まで残り</div>
              <div>
                  <p class="display-4 text--primary">
                  {{ remainMinutes }}
                  </p>
              </div>
              <div class="display-2 text--primary">
                  分あります。                
              </div>
            </v-card-text>
          </v-card>  
        </v-col></v-row>
        <v-row><v-col>
          <v-spacer />
        </v-col></v-row>
        <v-row><v-col>
            <v-card
      　      class="mx-auto"
              cols="12"
            >
              <v-card-title>
                {{ year }} 年まで残り何分かお伝えします。
              </v-card-title>
              <v-card-text>
                <blockquote class="blockquote">
                  &#8221;Five hundred twenty-five thousand six hundred minutes<br>
                   How Do you measure, measure a Year?&#8221;
                  <footer>
                    <small>
                      <em>&mdash;RENT Seasons of Love</em>
                    </small>
                  </footer>
                </blockquote>
              </v-card-text>
              <v-card-actions>
                <v-spacer />
              </v-card-actions>
            </v-card>
        </v-col></v-row>
    </v-flex>
  </v-layout>
</template>

<script>
import Logo from '~/components/Logo.vue'
import VuetifyLogo from '~/components/VuetifyLogo.vue'

export default {
  components: {
    Logo,
    VuetifyLogo
  },
  data: () =>({
    now: "525600",
    year: (new Date().getFullYear()+1)
  }),
  computed: {
    remainMinutes(){
      const year = new Date().getFullYear()
      //今年の元旦
      const newYearsDay = new Date(year,0,0,0,0)
      //現在の時刻
      const nowDate = new Date()
      //元旦から何分経過したか
      const howLongMinutes = (nowDate - newYearsDay)/1000/60
      
      //閏年か？
      let minutesOfYear = 0
      if( ((year%4 === 0) && (year%100 !== 0)) || (year%400 === 0) ){
        minutesOfYear = 60 * 24 * 366
      } else {
        minutesOfYear = 60 * 24 * 365
      }
      //525600minから経過時間を引き算する
      //console.log(minutesOfYear + " - " + howLongMinutes + "=" + (minutesOfYear - howLongMinutes))
      return Math.ceil(minutesOfYear - howLongMinutes).toLocaleString()
    }
  }
}
</script>
