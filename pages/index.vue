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
      <div class="text-center">
        <logo />
        <VuetifyLogo />
        {{ remainMinutes }}
      </div>
      <v-card>
        <v-card-title class="headline">
          {{ new Date().getFullYear()+1 }} 年まで残り何分かお伝えします。
        </v-card-title>
        <v-card-text>
          <blockquote class="blockquote">
            &#8221;525600 minutes How Do you measure? Measure a Year?&#8221;
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
    month: 0
  }),
  computed: {
    remainMinutes(){
      this.month = new Date()
      const year = new Date().getFullYear()
      //今年の元旦
      //現在の時刻
      //元旦から何分経過したか
      //閏年か？
      //525600minから経過時間を引き算する
      
      return this.month
    }
  }
}
</script>
