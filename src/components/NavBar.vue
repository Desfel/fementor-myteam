<template>
  <header class="navbar" :class="{ offline: !networkOnLine }">
    <router-link to="/home" class="logo">
      <img alt="logo-myteam" src="@/assets/img/logo.svg" />
    </router-link>

    <div class="links desktop-links">
      <nav class="nav-links">
        <div class="nav-item">
          <router-link to="/home">home</router-link>
          <router-link to="/about">about</router-link>
        </div>

        <router-link class="site-btn outlined-light" to="/contact">contact us</router-link>
      </nav>
    </div>

    <a href="#" class="burger-menu" @click="openMenu">
      <img src="@/assets/img/icon-hamburger.svg" />
    </a>

    <div class="mobile-menu-wrapper" :class="{'is-opened': menuIsActive}">
      <div class="mobile-menu">
        <a href="#" class="close-btn" @click="openMenu">
          <img src="@/assets/img/icon-close.svg" />
        </a>

        <nav class="nav-links">
          <div class="nav-item">
            <router-link to="/home" @click.native="openMenu">home</router-link>
            <router-link to="/about" @click.native="openMenu">about</router-link>
          </div>

          <router-link class="site-btn outlined-light" to="/contact" @click.native="openMenu">contact us</router-link>
        </nav>
      </div>
    </div>
  </header>
</template>

<script>
import { mapState } from 'vuex'

export default {
  data() {
    return {
      menuIsActive: false
    }
  },
  computed: {
    ...mapState('app', ['networkOnLine', 'appTitle', 'appShortTitle'])
  },
  methods: {
    openMenu(e) {
      e.preventDefault()
      this.menuIsActive = !this.menuIsActive
    }
  }
}
</script>

<style lang="scss" scoped>
@import '@/theme/variables.scss';

.navbar {
  display: flex;
  align-items: center;
  padding: $generalDesktopPadding;
  width: 100%;

  @media (max-width: 1024px) {
    padding: 0 40px;
  }

  @media (max-width: 767px) {
    padding: $generalMobilePadding;
  }

  .logo {
    margin-right: 80px;
  }

  .links {
    width: 100%;

    &.desktop-links {
      @media (max-width: 767px) {
        display: none;
      }
    }
  }

  .nav-links {
    display: flex;
    align-items: center;
    flex-grow: 1;
  }

  .burger-menu {
    display: none;
    text-align: right;
    margin-left: auto;

    @media (max-width: 767px) {
      display: block;
    }
  }

  .nav-item {
    a {
      font-weight: 600;
      font-size: 18px;
      line-height: 28px;
      color: $white;
      transition: color .3s ease-in-out;

      &:not(:last-child) {
        margin-right: 40px;
      }

      &:hover {
        color: $primaryColor2;
      }
    }
  }

  .site-btn {
    margin-left: auto;
  }

  .mobile-menu-wrapper {
    position: absolute;
    top: 0;
    left: 0;

    display: block;
    height: 100vh;
    width: 100%;

    background: rgba(0, 0, 0, 0);
    transition: all .3s ease-in-out;
    z-index: -1;
    overflow: hidden;

    &.is-opened {
      background: rgba(0, 0, 0, 0.5);
      z-index: 10;

      .mobile-menu {
        right: 0;
      }
    }

    .mobile-menu {
      position: absolute;
      top: 0;
      right: -255px;
      padding: 56px 25px 0 48px;

      display: flex;
      flex-direction: column;
      width: 255px;
      height: 100vh;

      background: $secondaryColor2;
      transition: right .3s ease-in-out;
      z-index: 11;

      overflow: hidden;

      &:before {
        content: '';
        position: absolute;
        bottom: 0;
        right: -100px;

        display: block;
        width: 200px;
        height: 200px;
        background: url('../assets/img/bg-pattern-about-1-mobile-nav-1.svg') top left/contain no-repeat;
      }

      .nav-links {
        margin-top: 39px;
        flex-direction: column;
        align-items: flex-start;

        .nav-item {
          display: flex;
          flex-direction: column;

          a {
            margin-bottom: 34px;
          }
        }

        .site-btn {
          margin: 0;
        }
      }
    }

    .close-btn {
      margin-left: auto;
    }
  }
}
</style>
