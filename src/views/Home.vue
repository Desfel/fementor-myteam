<template>
  <section class="page-wrapper">
    <section class="intro-section">
      <h1>
        Find the <br />best <span>talent</span>
      </h1>

      <div class="text-w-border">
        <span class="border"></span>

        <p class="body-1">
          Finding the right people and building high performing teams can be hard. Most companies aren’t tapping into
          the abundance of global talent. We’re about to change that.
        </p>
      </div>
    </section>

    <section class="build-section">
      <div class="content-wrapper">
        <div class="left-content text-w-border">
          <span class="border"></span>

          <h2>
            Build & manage distributed teams like no one else.
          </h2>
        </div>

        <div class="right-content">
          <div class="argument-block">
            <img src="@/assets/img/icon-person.svg" alt="Person" />

            <div class="argument-content">
              <p class="argument-title body-1">
                Experienced Individuals
              </p>
              <p class="body-2">
                Our network is made up of highly experienced professionals who are passionate about what they do.
              </p>
            </div>
          </div>
          <div class="argument-block">
            <img src="@/assets/img/icon-cog.svg" alt="Cog" />

            <div class="argument-content">
              <p class="argument-title body-1">
                Easy to Implement
              </p>
              <p class="body-2">
                Our processes have been refined over years of implementation meaning our teams always deliver.
              </p>
            </div>
          </div>
          <div class="argument-block">
            <img src="@/assets/img/icon-chart.svg" alt="Chart" />

            <div class="argument-content">
              <p class="argument-title body-1">
                Enhanced Productivity
              </p>
              <p class="body-2">
                Our customized platform with in-built analytics helps you manage your distributed teams.
              </p>
            </div>
          </div>
        </div>
      </div>
    </section>

    <section class="testimony-section">
      <h2>
        Delivering real results for top companies. Some of our <span>success stories</span>.
      </h2>

      <div class="testimonies">
        <div class="testimony">
          <p class="quote body-2">
            “The team perfectly fit the specialized skill set required. They focused on the most essential features
            helping us launch the platform eight months faster than planned.”
          </p>

          <p class="author body-1">
            Kady Baker
          </p>
          <p class="author-job">
            Product Manager at Bookmark
          </p>

          <img src="@/assets/img/avatar-kady.jpg" alt="Kady Baker" />
        </div>
        <div class="testimony">
          <p class="quote body-2">
            “We needed to automate our entire onboarding process. The team came in and built out the whole journey.
            Since going live, user retention has gone through the roof!”
          </p>

          <p class="author body-1">
            Aiysha Reese
          </p>
          <p class="author-job">
            Founder of Manage
          </p>

          <img src="@/assets/img/avatar-aiysha.jpg" alt="Aiysha Reese" />
        </div>
        <div class="testimony">
          <p class="quote body-2">
            “Amazing. Our team helped us build an app that delivered a new experience for hiring a physio. The launch
            was an instant success with 100k downloads in the first month.”
          </p>

          <p class="author body-1">
            Arthur Clarke
          </p>
          <p class="author-job">
            Co-founder of MyPhysio
          </p>

          <img src="@/assets/img/avatar-arthur.jpg" alt="Arthur Clarke" />
        </div>
      </div>
    </section>

    <contact></contact>
  </section>
</template>

<script>
import Contact from '@/components/Contact'
import { mapState } from 'vuex'

export default {
  components: { Contact },
  head() {
    return {
      title: {
        inner: 'Home'
      },
      meta: [
        {
          name: 'description',
          content: `${this.appTitle} home page`,
          id: 'desc'
        }
      ]
    }
  },
  computed: mapState('app', ['appTitle'])
}
</script>

<style lang="scss" scoped>
@import '@/theme/variables.scss';
@import '@/theme/home.scss';

.page-wrapper {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
</style>
