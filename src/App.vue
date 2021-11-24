<template>
  <div id="app">
    <div class="main-wrapper">
      <nav-bar></nav-bar>
      <router-view />
      <footer-component></footer-component>
    </div>

    <new-content-available-toastr
      v-if="newContentAvailable"
      class="new-content-available-toastr"
      :refreshing-app="refreshingApp"
      @refresh="serviceWorkerSkipWaiting"
    ></new-content-available-toastr>
    <apple-add-to-home-screen-modal
      v-if="showAddToHomeScreenModalForApple"
      class="apple-add-to-home-screen-modal"
      @close="closeAddToHomeScreenModalForApple(false)"
    >
    </apple-add-to-home-screen-modal>
  </div>
</template>
<script>
import NavBar from '@/components/NavBar'
import FooterComponent from '@/components/Footer'
import NewContentAvailableToastr from '@/components/NewContentAvailableToastr'
import AppleAddToHomeScreenModal from '@/components/AppleAddToHomeScreenModal'
import { mapState, mapActions, mapGetters } from 'vuex'

export default {
  components: { NavBar, NewContentAvailableToastr, AppleAddToHomeScreenModal, FooterComponent },
  computed: {
    ...mapGetters('app', ['newContentAvailable']),
    ...mapState('app', ['showAddToHomeScreenModalForApple', 'refreshingApp'])
  },
  methods: mapActions('app', [
    'closeAddToHomeScreenModalForApple',
    'serviceWorkerSkipWaiting'
  ])
}
</script>

<style lang="scss">
@import '@/theme/variables.scss';

html {
  scroll-behavior: smooth;
}

body {
  margin: 0;

  * {
    box-sizing: border-box;
  }

  img {
    vertical-align: middle;
  }

  p,
  h1,
  h2,
  h3,
  a {
    font-family: $textFont;
    margin: 0;
  }

  h1 {
    font-weight: bold;
    font-size: 100px;
    line-height: 100px;

    @media (max-width: 1200px) {
      font-size: 80px;
      line-height: 80px;
    }

    @media (max-width: 1024px) {
      font-size: 64px;
      line-height: 56px;
    }

    @media (max-width: 767px) {
      font-size: 40px;
      line-height: 40px;
    }

    .small-title {
      font-size: 64px;
      line-height: 100px;
    }
  }

  h2 {
    font-weight: bold;
    font-size: 48px;
    line-height: 48px;

    @media (max-width: 1024px) {
      font-size: 32px;
      line-height: 32px;
    }
  }

  h3 {
    font-weight: bold;
    font-size: 18px;
    line-height: 28px;
  }

  p {
    font-weight: 600;

    &.body-1 {
      font-size: 18px;
      line-height: 28px;
    }

    &.body-2 {
      font-size: 15px;
      line-height: 25px;
    }
  }

  a {
    text-decoration: none;
  }

  .site-btn {
    padding: 9px 33px 11px 32px;
    font-weight: 600;
    font-size: 18px;
    line-height: 28px;
    border-radius: 24px;
    border: 2px solid $white;
    transition: all 0.3s ease-in-out;

    &.outlined-light {
      background: transparent;
      color: $white;

      &:hover {
        background: $white;
        color: $secondaryColor5;
      }
    }

    &.outlined-dark {
      background: transparent;
      border-color: $secondaryColor5;
      color: $secondaryColor5;

      &:hover {
        background: $secondaryColor5;
        color: $white;
      }
    }

    &.filled {
      background: $white;
      color: $secondaryColor5;

      &:hover {
        border-color: $secondaryColor1;
        background: $secondaryColor1;
      }
    }

    &.is-disabled {
      opacity: 0.25;
      pointer-events: none;
    }
  }

  .text-w-border {
    display: flex;
    flex-direction: column;
    position: relative;

    .border {
      width: 50px;
      height: 4px;
    }
  }

  #app {
    font-family: -apple-system, BlinkMacSystemFont, Segoe UI, Roboto, Oxygen,
      Ubuntu, Cantarell, Fira Sans, Droid Sans, Helvetica Neue, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    font-size: 16px;
    color: #2c3e50;

    .new-content-available-toastr {
      position: absolute;
      bottom: 10px;
      right: 10px;
    }

    .main-wrapper {
      padding-top: 73px;
      min-height: 100vh;
      height: 100%;
      background: $primaryColor1;

      @media (max-width: 1024px) {
        padding-top: 64px;
      }

      @media (max-width: 767px) {
        padding-top: 48px;
      }

      .page-wrapper {
        margin: auto;
      }
    }
  }
}
</style>
