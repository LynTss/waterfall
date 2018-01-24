<template>
  <div class="template-wrap">
    <div style="position:fixed; top: 10px; left: 50%; z-index:999999">{{total1}}/{{total2}}/{{total3}}/{{total4}}/{{total5}}</div>
    <div class="masonry">
      <div v-if="firstList.length === 0 && secondList.length === 0 && thirdList.length === 0 && fourthList.length === 0 && fifthList.length === 0">
        没有搜索结果
        <button @click="searchSet">123123</button>
      </div>
      <div v-else>
        <div class="searchList List1" id="List1">
          <searchCard v-for="(se,index) in firstList" :urlAddress="se.urlAddress" :key="index"></searchCard>
        </div>
        <div class="searchList List2" id="List2">
          <searchCard v-for="(se,index) in secondList" :urlAddress="se.urlAddress" :key="index"></searchCard>
        </div>
        <div class="searchList List3" id="List3">
          <searchCard v-for="(se,index) in thirdList" :urlAddress="se.urlAddress" :key="index"></searchCard>
        </div>
        <div class="searchList List4" id="List4">
          <searchCard v-for="(se,index) in fourthList" :urlAddress="se.urlAddress" :key="index"></searchCard>
        </div>
        <div class="searchList List5" id="List5">
          <searchCard v-for="(se,index) in fifthList" :urlAddress="se.urlAddress" :key="index"></searchCard>
        </div>
        <div class="loading loading-circle bottom-loading"></div>
      </div>
    </div>
  </div>
</template>

<script>
  import searchCard from './searchCard.vue'
  export default {
    data () {
      return {
        firstList: [],
        secondList: [],
        thirdList: [],
        fourthList: [],
        fifthList: [],
        searchList: [
          {
            urlAddress: '//hbimg-other.b0.upaiyun.com/f9902330e763f3ab166d05334c5462c1659da153c799_fw236',
            imgHeight: 399
          }, {
            urlAddress: 'http://tpc.googlesyndication.com/daca_images/simgad/15186292091171188100?w=400&h=209',
            imgHeight: 117
          }, {
            urlAddress: '//img.hb.aicdn.com/700048ae5111f94d0ff4163dd961b5dc253455d8afebd-tTqBtg_fw236',
            imgHeight: 337
          }, {
            urlAddress: '//img.hb.aicdn.com/cfc0473b5cc468a7a9a7e74cc727276fa706b062664a3-3YTDjo_fw236',
            imgHeight: 336
          }, {
            urlAddress: '//img.hb.aicdn.com/ad9488fc71949dc1318ddcd3a6e6c79b381d4be326d8a-cAvQdg_fw236',
            imgHeight: 150
          }, {
            urlAddress: '//img.hb.aicdn.com/049c5ced19b54224b76e55a35ad3dd7884cf02a9538ce-5ZT4yt_fw236',
            imgHeight: 149
          }, {
            urlAddress: '//img.hb.aicdn.com/23e5ca244f8ad95aad924061ab81bce6edb4ca6b38110-aeToUs_fw236',
            imgHeight: 224
          }, {
            urlAddress: '//img.hb.aicdn.com/34d1882b22b9178ce46c669adefa54c7f39ddc0b21353-tw5Qzp_fw236',
            imgHeight: 504
          }, {
            urlAddress: '//img.hb.aicdn.com/2f31f2c917c94a9b46b6bef263eacbbebbddadcc4eec7-9PECY7_fw236',
            imgHeight: 324
          }, {
            urlAddress: '//img.hb.aicdn.com/8a5f0a250e02763ca7c150e83ef2bbf5bb0e4e601859e-uRjOWz_fw236',
            imgHeight: 336
          }, {
            urlAddress: '//img.hb.aicdn.com/32408c878271bde8dd1bc3bbca0ba3236f710d6c9493-XbrWsm_fw236',
            imgHeight: 126
          }, {
            urlAddress: '//img.hb.aicdn.com/c4ac98fe472d8289e97d7fed3794a7ccaf6475a52a939-yY1H66_fw236',
            imgHeight: 290
          }, {
            urlAddress: '//img.hb.aicdn.com/6c90c3dc22f0522b4b1b36382be5d35ddfc4c51831b6d-rTEaIA_fw236',
            imgHeight: 224
          }, {
            urlAddress: '//img.hb.aicdn.com/f3a7160702a1d6e1db392ae55174b172bab17d661ffe6-uDb30Q_fw236',
            imgHeight: 317
          }, {
            urlAddress: '//img.hb.aicdn.com/c22265ae1eb431ff4a1b6bc21e8360236970409d16dea-Kf3CEr_fw236',
            imgHeight: 126
          }, {
            urlAddress: '//img.hb.aicdn.com/535e6466d970b1a36a8cb054093a2d27cbac3b827932-bFeYU0_fw236',
            imgHeight: 104
          }
        ],
        total1: 0,
        total2: 0,
        total3: 0,
        total4: 0,
        total5: 0
      }
    },
    components: {
      searchCard
    },
    mounted: function () {
      window.onscroll = function () {
        if (this.getScrollTop() + this.getClientHeight() >= this.getScrollHeight() - 100) {
          if (this.timer) {
            clearTimeout(this.timer)
          }
          this.timer = setTimeout(() => {
            this.searchSet()
          }, 500)
        }
      }.bind(this)
    },
    created () {
    },
    methods: {
      searchSet () {
        let total1 = Number(this.total1)
        let total2 = Number(this.total2)
        let total3 = Number(this.total3)
        let total4 = Number(this.total4)
        let total5 = Number(this.total5)
        for (let se of this.searchList) {
          let heightMin = Math.min(total1, total2, total3, total4, total5)
          if (heightMin === total1) {
            this.firstList.push(se)
            total1 = total1 + se.imgHeight
            console.log(total1)
          } else if (heightMin === total2) {
            this.secondList.push(se)
            total2 = total2 + se.imgHeight
            console.log(total2)
          } else if (heightMin === total3) {
            this.thirdList.push(se)
            total3 = total3 + se.imgHeight
            console.log(total3)
          } else if (heightMin === total4) {
            this.fourthList.push(se)
            total4 = total4 + se.imgHeight
            console.log(total4)
          } else if (heightMin === total5) {
            this.fifthList.push(se)
            total5 = total5 + se.imgHeight
            console.log(total5)
          }
        }
        this.total1 = total1
        this.total2 = total2
        this.total3 = total3
        this.total4 = total4
        this.total5 = total5
      },
      // 获取当前滚动高度
      getScrollTop () {
        let scrollTop = 0
        if (document.documentElement && document.documentElement.scrollTop) {
          scrollTop = document.documentElement.scrollTop
        } else if (document.body) {
          scrollTop = document.body.scrollTop
        }
        return scrollTop
      },
      // 获取当前可视范围的高度
      getClientHeight () {
        let clientHeight = 0
        if (document.body.clientHeight && document.documentElement.clientHeight) {
          clientHeight = Math.min(document.body.clientHeight, document.documentElement.clientHeight)
        } else {
          clientHeight = Math.max(document.body.clientHeight, document.documentElement.clientHeight)
        }
        return clientHeight
      },
      // 获取文档完整的高度
      getScrollHeight () {
        return Math.max(document.body.scrollHeight, document.documentElement.scrollHeight)
      }
    }
  }
</script>

<style lang="less" rel="stylesheet/less">

.template-wrap{
  width: 1200px;
  padding-top: 20px;
  margin: 0 auto;
}
.masonry {
  width: 100%;
  overflow: hidden;
  .searchList {
    width: 224px;
    display: block;
    float: left;
    margin-right: 20px;
    &:nth-child(5){
      margin: 0;
    }
  }
}
.bottom-loading{
  margin: 40px auto;
}
</style>
