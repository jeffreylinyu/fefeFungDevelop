<template>
  <!-- Footer -->
  <footer id="bk-footer"
  class="page-footer bg_color--3 pl--150 pr--150 pl_lg--30 pr_lg--30 pl_md--30 pr_md--30 pl_sm--5 pr_sm--5" style="background: #000000;">
  <!-- Start Footer Top Area -->
  <div class="bk-footer-inner pt--50 pb--30 pt_sm--80">
      <div class="container">
          <div class="row">

              <div class="col-lg-4 col-md-6 col-sm-6 col-12 mt_md--40 mt_sm--40">
                  <div class="footer-widget text-var--2 menu--contact">
                      <h2 class="widgettitle">{{ allData[1].title }}</h2>
                      <div class="footer-address">
                          <div class="bk-hover">
                              <p>{{ allData[1].content }}</p>
                              <p>{{ allData[2].content }}</p>
                          </div>
                      </div>
                  </div>
                  <div class="footer-widget text-var--2 menu--contact">
                      <h2 class="widgettitle">{{ allData[4].title }}</h2>
                      <div class="footer-address">
                          <div class="bk-hover">
                              <p style="white-space: pre-line;">{{ allData[4].content }}</p>

                          </div>
                      </div>
                  </div>
              </div>

              <div class="col-lg-5 col-md-6 col-sm-6 col-12 mt_md--40 mt_sm--40">
                  <div class="footer-widget text-var--2 menu--contact">
                      <h2 class="widgettitle">{{ allData[3].title }}</h2>
                      <div class="footer-address">
                          <div class="bk-hover">
                              <p style="white-space: pre-line;">{{ allData[3].content }}</p>
                          </div>


                      </div>
                  </div>
              </div>

              <div class="col-lg-3 col-md-6 col-sm-6 col-12 mt_md--40 mt_sm--40">
                  <div class="footer-widget text-var--2 menu--instagram">
                      <div style="max-width:70%;">
                          <img src="/img/home-logo-W.svg" alt="">
                      </div>
                      <div class="social-share social--transparent text-white mt--20 mb--20">
                          <a href="https://www.facebook.com/DaxiTakoham"><i class="fab fa-facebook"></i></a>
                          <a href="https://www.youtube.com/channel/UCX_5DKCU3VDqPcyQLyhT2Hg"><i class="fab fa-youtube"></i></a>
                      </div>
                      <div >
                          <img style="max-width:70%; margin: 0 auto;" src="/img/footer-icon.png" alt="">
                      </div>
                  </div>
              </div>

          </div>
      </div>
  </div>
  <!-- Start Footer Top Area -->

  <!-- Start Copyright Area -->
  <div class="copyright ptb--15 text-var-2">
      <div class="container">
          <div class="row align-items-center">
              <div class="col-lg-12 col-md-6 col-sm-12 col-12">
                  <div class="copyright-right text-md-left text-center">
                      <p>鳳飛飛故事館 版權所有 Copyright (C) 2021</p>
                      <p>建議解析度：1280x720以上　瀏覽器支援：Chrome、Firefox、Edge、Safari，Win7已不再支援IE，Win10將於2022年6月15日淘汰並停止支援IE。
                      </p>
                  </div>
              </div>
          </div>
      </div>
  </div>

  <loading v-if="isLoading" />
  <!-- End Copyright Area -->
  </footer>
  <!--// Footer -->
</template>

<script>
// import $ from 'jquery'
// import myMain from '@/static/js/main.js';
// import myRevoulation from '@/static/js/revoulation.js';

export default {
  auth: false,
  layout: 'default',
  components: {
    loading: require('~/components/loading.vue').default,
  },
  props: {

  },
  data () {
    return {
      isLoading: false,
      allData: []
    }
  },
  created() {
    for(let i = 0; i < 30; i++) {
      this.allData.push({
        auth: null,
        category: null,
        content: null,
        image: null,
        indexR: null,
        module: null,
        postDate: null,
        remark: null,
        states: null,
        title: null,
        url: null
      })
    }
  },
  mounted () {
    this.getData()
    // myMain()
    // myRevoulation()
  },
  destroyed () {

  },
  computed: {

  },
  methods: {
    getData() {
      this.isLoading = true
      this.$axios.get(`/api/func/content/module/A03`)
        .then( res => {
          this.isLoading = false
          this.allData = res.data.data
          console.log(this.allData)
          this.isLoading = false

        })
        .catch(res => {
          console.log(res)
          this.isLoading = false
        })
    }
  }
}
</script>


<style lang="scss" scoped>

.default {

}

</style>
