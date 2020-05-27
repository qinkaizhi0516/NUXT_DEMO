import axios from 'axios';
<template>
  <div>
    <section>
      <!-- banner -->
      <b-card overlay img-src="/images/banner_jokes.jpg" title="Jokes Page" class="jokes-banner">
        <b-card-text>
          This is a jokes page!
        </b-card-text>
      </b-card>

      <!-- search -->
      <div class="search-box">
        <b-input-group prepend="Search" class="mt-3">
          <b-form-input placeholder="please enter a joke's text" v-model="searchWords">
          </b-form-input>
        </b-input-group>
        <b-input-group prepend="Limit" class="mt-3">
          <b-form-input placeholder="please enter page's limit" v-model="perPage">
          </b-form-input>
        </b-input-group>
        <b-button block class="mt-3" variant="info" @click="getJokesData"> Click Search Jokes</b-button>
      </div>

      <!-- jokes list -->
      <div class="jokes-list-box">
        <b-list-group>
          <b-list-group-item v-for="(item, index) in jokes" :key="index" class="mt-3">{{ item }}</b-list-group-item>
        </b-list-group>
      </div>

      <!-- loading-box -->
      <div class="loading-box" v-if="jokes.length === 0">
        <h2>Loading......</h2>
      </div>

      <!-- pagination -->
      <div class="pagination">
        <b-pagination v-model="page" :total-rows="rows" :per-page="perPage" first-text="First" last-text="Last"
          prev-text="prev" next-text="next" align="center" @click.native="getJokesData">
        </b-pagination>
      </div>
    </section>
  </div>
</template>

<script>
  import axios from 'axios'
  export default {
    name: 'Jokes',
    head() {
      return {
        title: 'Jokes query search page .',
        meta: [{
          hid: 'description',
          name: 'description',
          content: 'This is jokes query search page'
        }]
      }
    },
    data() {
      return {
        searchWords: "",
        perPage: 10,
        page: 1,
        rows: 0,
        jokes: []
      }
    },
    created() {
      this.getJokesData();
    },
    methods: {
      async getJokesData() {
        let config = {
          _page: this.page,
          _limit: this.perPage,
          q: this.searchWords
        }
        const res = await axios.get('http://localhost:3002/jokes', {
          params: config
        })
        console.log(res)
        this.jokes = res.data.map(e => e.joke);
        this.rows = res.headers['x-total-count'];
      }
    }
  }

</script>

<style lang="scss" scoped>
  .jokes-banner {
    border: 0;
    border-radius: 0;
    color: #ffffff;
  }

  .search-box {
    width: 96%;
    height: auto;
    margin: 0 auto;
    padding-bottom: 20px;
  }

  .loading-box {
    text-align: center;
    margin: 10px auto;
  }

  .jokes-list-box {
    width: 96%;
    margin: 0 auto;
  }

  .pagination {
    margin: 30px auto;
  }

</style>
