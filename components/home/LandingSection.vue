<template>
  <section class="landing-section">
    <the-text-animation></the-text-animation>
    <h1>{{ $t('home.landingSection.title') }}</h1>
    <nuxt-link class="landing-button" :to="localePath('contact-me')">
      <app-button width="100%" :text="$t('links.contact')"></app-button>
    </nuxt-link>
    <app-button-scroll></app-button-scroll>
  </section>
</template>

<script>
import AppButton from '@/components/shared/AppButton'
import TheTextAnimation from '@/components/home/TheTextAnimation'
import AppButtonScroll from '@/components/shared/AppButtonScroll'

export default {
  components: {
    AppButton,
    TheTextAnimation,
    AppButtonScroll
  }
}
</script>

<style lang="scss" scoped>
.landing-section {
  width: 100%;
  height: 100vh;
  background: $site-gray url('~assets/images/dots.svg') no-repeat center center;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
  text-align: center;
  position: relative;
}

h1 {
  color: transparent;
  font-size: 45px;
  margin: 20px 10px;
  color: white;
}

.landing-button {
  width: 30% !important;
  min-width: 240px;
  max-width: 550px;
}

@media screen and (max-width: 600px) {
  .landing-section {
    h1 {
      font-size: 35px;
      span {
        font-size: 45px;
      }
    }
  }
}

@media screen and (max-width: 400px) {
  .landing-section {
    h1 {
      font-size: 25px;
      span {
        font-size: 35px;
      }
    }
  }
}
</style>