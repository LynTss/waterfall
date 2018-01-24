<template>
    <div class="item">
        <div class="item_content">
            <img class="item_img" :src="this.urlAddress" alt="">
        </div>
    </div>
</template>

<script>
  export default {
    data () {
      return {
      }
    },
    props: [
      'urlAddress'
    ],
    components: {
    },
    created () {
    },
    methods: {
    }
  }
</script>

<style lang="less" rel="stylesheet/less">
.item {
    -webkit-box-sizing: border-box;
            box-sizing: border-box;
    width: 100%;
    margin-bottom: 20px;
  .item_content {
    position: relative;
    display: block;
    background: currentColor;
    -webkit-box-sizing: border-box;
            box-sizing: border-box;
      transition-duration: .2s;
    &:hover {
      box-shadow: 0 0 10px #333;
      cursor: pointer
    }
    .item_img{
      width: 100%;
    }
  }
}
</style>
