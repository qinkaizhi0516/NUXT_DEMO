<template>
  <div>
    <section class="content-page">
      <!-- 轮播组件 -->
      <b-carousel :interval="3000" img-width="1024" img-height="480" fade indicators
        style="text-shadow:1px 1px 2px #333">
        <b-carousel-slide v-for="(item, index) in sliders" :key="index" :caption="item.subTitle"
          :v-text="item.subtTitle1" :img-src="item.imgSrc">

        </b-carousel-slide>
      </b-carousel>

      <!-- 标题组件 -->
      <h1 class="index-title" align="center">Damon jokes
        <span class="badge badge-secondary"> New</span>
      </h1>

      <!-- 列表 -->

      <div class="card-info">
        <b-card-group v-for="(item, index) in jokes" :key="index">
          <b-card>
            <b-card-text> {{ item }}</b-card-text>
          </b-card>
        </b-card-group>
      </div>
    </section>
  </div>
</template>

<script>
  import axios from 'axios'
  export default {
    name: 'Home',
    head() {
      return {
        title: 'Index Page-Damon-Jokes',
        meta: [{
          hid: 'description',
          name: 'description',
          content: 'This is a funny jokes home page'
        }]
      }
    },
    data() {
      return {
        sliders: [{
            caption: 'Title1',
            text: "subTitle1",
            imgSrc: '/images/slider_01.jpg'
          },
          {
            caption: 'Title2',
            text: "subTitle2",
            imgSrc: '/images/slider_02.jpg'
          },
          {
            caption: 'Title3',
            text: "subTitle3",
            imgSrc: '/images/slider_03.jpg'
          },
        ],
        jokes: []
      }
    },
    asyncData(context) {
      console.log("Data -> context", context)
      // const res = await axios.get('http://localhost:3002/jokes?_limit=20')
      // let jokes = res.data.map(e => e.joke)
      // return {
      //   jokes: jokes
      // }
    },
    // async created(){
    //   const res = await axios.get('http://localhost:3002/jokes?_limit=20')
    //   let jokes = res.data.map(e => e.joke)
    //   this.jokes = jokes;
    // }
  }

</script>

<style scoped>
  .content-page {
    margin: 0;
    width: 100%;
  }

  h1 {
    margin: 10px auto;
  }

  .card-info {
    width: 92%;
    margin: 0 auto;
    margin-bottom: 30px;
  }

</style>
