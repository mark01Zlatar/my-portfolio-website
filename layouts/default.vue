<template>
  <div>
    <app-header></app-header>
    <nuxt />
    <app-footer v-if="$route.path !== localePath('contact-me')"></app-footer>
    <app-cookie-banner v-if="!$store.getters.isCookiesAccepted"></app-cookie-banner>
  </div>
</template>

<script>
import AppHeader from '@/components/shared/AppHeader'
import AppFooter from '@/components/shared/AppFooter'
import AppCookieBanner from '@/components/shared/AppCookieBanner'
import { bootstrap } from "vue-gtag"

export default {
  head() {
    return this.$nuxtI18nSeo()
  },
  components: {
    AppHeader,
    AppFooter,
    AppCookieBanner
  },
  watch: {
    '$route.path': function(value) {
      this.$store.commit('SET_MOBILE_NAVBAR', false)
    }
  },
  mounted() {
    this.cookiesAccepted = JSON.parse(localStorage.getItem('cookiesAccepted'))

    this.$store.commit('SET_COOKIES_ACCEPTED', this.cookiesAccepted);

    if(this.cookiesAccepted) {
      bootstrap().then(gtag => {
      });
    }

    this.$nextTick(() => {
      this.$nuxt.$loading.start()

      setTimeout(() => this.$nuxt.$loading.finish(), 500)
    })
  }
}
</script>

<style>
</style>
