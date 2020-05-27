<template>
  <div>
    <section>
      <b-card overlay img-src="/images/banner_about.jpg" title="Jokes Page" class="about-banner">
        <b-card-text>
          This is a about page!
        </b-card-text>
      </b-card>

      <!-- about-title -->
      <h1 class="index-title" align="center">About Page
        <span class="badge badge-secondary"> ABout</span>
      </h1>

      <!-- card list -->
      <div class="about-centent mt-3">
        <b-card-group>
          <b-card v-for="(item, index) in cards" :key="index" border-variant="info" text-variant="#333"
            :header="item.header" class="text-center">
            <b-card-text v-html="item.content"></b-card-text>
          </b-card>
        </b-card-group>
      </div>
    </section>
  </div>
</template>

<script>
  export default {
    name: 'About',
    head() {
      return {
        title: 'Jokes About Page.',
        meta: [{
          hid: 'description',
          name: 'description',
          content: 'This is my about page.'
        }]
      }
    },
    data() {
      return {
        cards: [{
            header: 'Jokes Api Website',
            content: 'URL <em>https://icanhazdadjoke.com/api/</em> get all joke api;'
          },
          {
            header: 'Jokes Api Website',
            content: 'URL <em>https://icanhazdadjoke.com/api/</em> get all joke api;'
          },
          {
            header: 'Jokes Api Website',
            content: 'URL <em>https://icanhazdadjoke.com/api/</em> get all joke api;'
          },
        ]
      }
    },
  }

</script>

<style lang="scss" scoped>
  .about-banner {
    border: 0;
    border-radius: 0;
    color: #ffffff;
  }

  h1 {
    margin: 10px auto;
  }

  .about-centent {
    width: 92%;
    margin: 0 auto;
    margin-bottom: 20px;
  }

</style>
