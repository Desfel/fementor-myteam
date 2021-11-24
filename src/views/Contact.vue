<template>
  <div class="page-wrapper">
    <section class="contact-section">
      <div class="contact-content">
        <h1 class="small-title">Contact</h1>
        <h2>Ask us about</h2>

        <div class="contact-reasons">
          <div class="contact-reason">
            <img src="@/assets/img/icon-person.svg" alt="Person" />
            <p class="body-1">The quality of our talent network</p>
          </div>

          <div class="contact-reason">
            <img src="@/assets/img/icon-cog.svg" alt="Cog" />
            <p class="body-1">Usage & implementation of our software</p>
          </div>

          <div class="contact-reason">
            <img src="@/assets/img/icon-chart.svg" alt="Chart" />
            <p class="body-1">How we help drive innovation</p>
          </div>
        </div>
      </div>

      <div class="contact-form-wrapper">
        <form class="contact-form" action="#" method="POST">
          <div class="input-wrapper">
            <div class="input-field">
              <input
                v-model="name"
                :class="{ 'is-error': invalidForm.name }"
                type="text"
                value=""
                name="name"
                placeholder="Name"
              />
            </div>

            <p v-if="invalidForm.name" class="error-message">
              This field is required
            </p>
          </div>

          <div class="input-wrapper">
            <div class="input-field">
              <input
                v-model="email"
                :class="{ 'is-error': invalidForm.email }"
                type="email"
                value=""
                name="email"
                placeholder="Email Address"
              />
            </div>
            <p v-if="invalidForm.email === 2" class="error-message">
              This field is required
            </p>
            <p v-else-if="invalidForm.email" class="error-message">
              Please use a valid email address
            </p>
          </div>

          <div class="input-wrapper">
            <div class="input-field">
              <input
                type="text"
                value=""
                name="company"
                placeholder="Company Name"
              />
            </div>
          </div>

          <div class="input-wrapper">
            <div class="input-field">
              <input
                type="text"
                value=""
                name="title"
                placeholder="Title"
              />
            </div>
          </div>

          <div class="input-wrapper">
            <div class="input-field">
              <textarea
                name="message"
                v-model="message"
                :class="{ 'is-error': invalidForm.message }"
                placeholder="Message"
              ></textarea>
            </div>

            <p v-if="invalidForm.message" class="error-message">
              This field is required
            </p>
          </div>

          <button class="site-btn filled" type="submit" @click="validateForm">
            Submit
          </button>
        </form>
      </div>
    </section>
  </div>
</template>

<script>
import { mapState } from 'vuex'

export default {
  data() {
    return {
      name: '',
      email: '',
      message: '',
      invalidForm: {
        name: false,
        email: false,
        message: false
      }
    }
  },
  head() {
    return {
      title: {
        inner: 'Contact Us'
      },
      meta: [
        {
          name: 'description',
          content: `${this.appTitle} about`,
          id: 'desc'
        }
      ]
    }
  },
  methods: {
    validateForm(e) {
      e.preventDefault()

      const emailRegex = /^(([^<>()[\]\\.,;:\s@"]+(\.[^<>()[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/
      const emailState = emailRegex.test(String(this.email).toLowerCase())

      this.invalidForm.email = this.email.trim() === '' ? 2 : !emailState
      this.invalidForm.name = this.name.trim() === ''
      this.invalidForm.message = this.message.trim() === ''

      console.log(this.invalidForm)
    }
  },
  computed: mapState('app', ['appTitle'])
}
</script>

<style lang="scss" scoped>
@import '@/theme/variables.scss';
@import '@/theme/contact.scss';

.page-wrapper {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;

  .logo {
    margin-bottom: 3rem;
  }

  .home-page-title {
    text-align: center;
  }

  .documentation-link {
    display: inline-block;
    font-size: 1.2rem;
    color: #fff;
    background-color: #5d6788;
    padding: 0.8rem 1.6rem;
    border-radius: 4px;
    transition: background-color 0.1s ease;
    box-sizing: border-box;
    text-decoration: none;
    width: fit-content;
    font-weight: 500;
  }
}
</style>
