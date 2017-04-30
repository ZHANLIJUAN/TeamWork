<template>
  <div class="banner-wrap">
    <div class="banner">
      <div class="container" :style="{left:leftImg + 'rem'}">
        <img @touchstart='handleTouchStart' @touchend='handleTouchEnd'v-for='item in listImg' :src="item.url">
      </div>
    </div>
    <div class="slide">
      <span @click='imgSwitch' index='1' v-for='(index,item) in listImg'></span>
    </div>
  </div>
</template>
<script>
import 'style/Banner.less'

export default {
  name: 'Home',
  data () {
    return {
      listImg: [{
        url: 'http://p.qpic.cn/qqconadmin/0/2d42638a39824e31a486240570454c71/0'
      }, {
        url: 'http://p.qpic.cn/qqconadmin/0/0416e2c1a76347b28d6095a84cdd7c50/0'
      }, {
        url: 'http://p.qpic.cn/qqconadmin/0/576acc73a2494af789d94841d17e1e0c/0'
      }, {
        url: 'http://p.qpic.cn/qqconadmin/0/4a36f17b249b468da84f6e3baf78c5bb/0'
      }, {
        url: 'http://p.qpic.cn/qqconadmin/0/de2054eaa59349c99e4bde63c4eb8cc5/0'
      }, {
        url: 'http://p.qpic.cn/qqconadmin/0/a2e988cdf14c40f8be6579cd68a80d84/0'
      }, {
        url: 'http://p.qpic.cn/qqconadmin/0/f51c23e1a4134fea849f1ef21036e478/0'
      }],
      leftImg: '0',
      pageX1: '',
      pageX2: ''
    }
  },
  methods: {
    imgSwitch (item) {
      this.leftImg = -item * 20
    },
    handleTouchStart (e) {
      var {changedTouches} = e
      var { pageX } = changedTouches[0]
      this.pageX1 = pageX
    },
    handleTouchEnd (e) {
      var {changedTouches} = e
      var {pageX} = changedTouches[0]
      this.pageX2 = pageX
      this.flag = this.pageX2 > this.pageX1

      if (this.pageX2 > this.pageX1) {
        this.leftImg = this.leftImg + 20
      } else {
        this.leftImg = this.leftImg - 20
      }
    }
  },
  created () {
    let _this = this
    setInterval(function () {
      if (_this.leftImg < -100) {
        _this.leftImg = 0
      }
      _this.leftImg = _this.leftImg - 20
    }, 2000)
  }
}
</script>
