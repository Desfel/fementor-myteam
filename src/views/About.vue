<template>
  <div class="page-wrapper">
    <section class="intro-section">
      <h1 class="small-title">
        About
      </h1>

      <div class="text-w-border">
        <span class="border"></span>

        <p class="body-1">
          We help companies build dynamic teams made up of top global talent. Using our network of passionate
          professionals we drive innovation and deliver incredible outcomes. Talented, diverse teams shape the best
          products and experiences. We’ll bring those teams to you.
        </p>
      </div>
    </section>

    <section class="team-section">
      <h2>Meet the directors</h2>

      <div class="team-wrapper">
        <div class="team-card" v-for="member in teamMembers" v-bind:key="member.id" :class="{'is-opened': openedCards.indexOf(member.id) !== -1}">
          <div class="front-card">
            <img class="avatar" :src="'../img/' + member.img" :alt=" member.name " />
            <p class="team-name body-1" v-text="member.name"></p>
            <p class="team-role body-2" v-text="member.role"></p>
          </div>

          <div class="back-card">
            <p class="team-name body-1" v-text="member.name"></p>
            <p class="team-text body-2" v-text="member.bio"></p>

            <div class="team-socials">
              <a href="#">
                <svg xmlns="http://www.w3.org/2000/svg" width="24" height="20"><path fill="#FFF" d="M24 2.557a9.83 9.83 0 01-2.828.775A4.932 4.932 0 0023.337.608a9.864 9.864 0 01-3.127 1.195A4.916 4.916 0 0016.616.248c-3.179 0-5.515 2.966-4.797 6.045A13.978 13.978 0 011.671 1.149a4.93 4.93 0 001.523 6.574 4.903 4.903 0 01-2.229-.616c-.054 2.281 1.581 4.415 3.949 4.89a4.935 4.935 0 01-2.224.084 4.928 4.928 0 004.6 3.419A9.9 9.9 0 010 17.54a13.94 13.94 0 007.548 2.212c9.142 0 14.307-7.721 13.995-14.646A10.025 10.025 0 0024 2.557z"/></svg>
              </a>
              <a href="#">
                <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20"><path fill="#FFF" d="M18 0H2C.9 0 0 .9 0 2v16c0 1.1.9 2 2 2h16c1.1 0 2-.9 2-2V2c0-1.1-.9-2-2-2zM6 17H3V8h3v9zM4.5 6.3c-1 0-1.8-.8-1.8-1.8s.8-1.8 1.8-1.8 1.8.8 1.8 1.8-.8 1.8-1.8 1.8zM17 17h-3v-5.3c0-.8-.7-1.5-1.5-1.5s-1.5.7-1.5 1.5V17H8V8h3v1.2c.5-.8 1.6-1.4 2.5-1.4 1.9 0 3.5 1.6 3.5 3.5V17z"/></svg>
              </a>
            </div>
          </div>

          <span class="card-trigger" :class="{'is-opened': openedCards.indexOf(member.id) !== -1}" @click="flipCard(member.id)"></span>
        </div>
      </div>
    </section>

    <section class="clients-section">
      <h2>Some of our clients</h2>

      <div class="clients">
        <div class="client" style="background-image:url('../img/logo-the-verge.png');"></div>
        <div class="client" style="background-image:url('../img/logo-jakarta-post.png');"></div>
        <div class="client" style="background-image:url('../img/logo-the-guardian.png');"></div>
        <div class="client" style="background-image:url('../img/logo-tech-radar.png');"></div>
        <div class="client" style="background-image:url('../img/logo-gadgets-now.png');"></div>
      </div>
    </section>

    <contact></contact>
  </div>
</template>

<script>
import Contact from '@/components/Contact'
import { mapState } from 'vuex'

export default {
  components: { Contact },
  data() {
    return {
      teamMembers: [
        {
          id: 1,
          name: 'Nikita Marks',
          role: 'Founder & CEO',
          bio:
            '“It always amazes me how much talent there is in every corner of the globe.”',
          img: 'avatar-nikita.jpg'
        },
        {
          id: 2,
          name: 'Cristian Duncan',
          role: 'Co-founder & COO',
          bio:
            '“Distributed teams required unique processes. You need to approach work in a new way.”',
          img: 'avatar-christian.jpg'
        },
        {
          id: 3,
          name: 'Cruz Hamer',
          role: 'Co-founder & CTO',
          bio:
            "“Technology is at the forefront of enabling distributed teams. That's where we come in.”",
          img: 'avatar-cruz.jpg'
        },
        {
          id: 4,
          name: 'Drake Heaton',
          role: 'Business Development Lead',
          bio:
            '“Hiring similar people from similar backgrounds is a surefire way to stunt innovation.”',
          img: 'avatar-drake.jpg'
        },
        {
          id: 5,
          name: 'Griffin Wise',
          role: 'Lead Marketing',
          bio:
            '“Unique perspectives shape unique products, which is what you need to survive these days.”',
          img: 'avatar-griffin.jpg'
        },
        {
          id: 6,
          name: 'Aden Allan',
          role: 'Head of Talent',
          bio:
            '“Empowered teams create truly amazing products. Set the north star and let them follow it.”',
          img: 'avatar-aden.jpg'
        }
      ],
      openedCards: []
    }
  },
  head() {
    return {
      title: {
        inner: 'About'
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
    flipCard(value) {
      console.log(value)

      if(this.openedCards.indexOf(value) === -1) {
        console.log('add')
        this.openedCards.push(value)
      } else {
        console.log('remove')
        this.openedCards.splice(this.openedCards.indexOf(value), 1);
      }

      console.log(this.openedCards)
    },
  },
  computed: mapState('app', ['appTitle'])
}
</script>

<style lang="scss" scoped>
@import '@/theme/variables.scss';
@import '@/theme/about.scss';

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
