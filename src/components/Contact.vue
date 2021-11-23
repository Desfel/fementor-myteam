<template>
  <section class="contact-cta-wrapper">
      <h2>Ready to get started?</h2>
      <router-link to="/contact" class="site-btn outlined-dark">Contact us</router-link>
  </section>
</template>

<style lang="scss" scoped>
@import '@/theme/variables.scss';

.contact-cta-wrapper {
  position: relative;
  display: flex;
  align-items: center;
  justify-content: center;
  width: 100%;
  padding: 76px 24px;
  background: $primaryColor2;

  @media (max-width: 1024px) {
    padding: 84px 24px;
  }

  @media (max-width: 767px) {
    flex-direction: column;
  }

  &:before {
    content: '';
    position: absolute;
    bottom: 0;
    left: 0;
    display: block;
    width: 200px;
    height: 122px;
    background: url('../assets/img/bg-pattern-home-6-about-5.svg') top left/contain no-repeat;
  }

  h2 {
    color: $secondaryColor5;

    @media (max-width: 767px) {
      text-align: center;
    }
  }

  .site-btn {
    margin-left: 16%;

    @media (max-width: 767px) {
      margin: 24px 0 0;
    }
  }
}
</style>
