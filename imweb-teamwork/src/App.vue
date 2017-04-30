<template>
  <div id="app" class="full">
    <top-header></top-header>
    <div class="wrap full">
      <banner></banner>
      <nav-comp></nav-comp>
      <ted></ted>
      <rank-wrap></rank-wrap>
      <footer-comp></footer-comp>
    </div>
  </div>
</template>

<script>
import 'style/App.less'
import Ted from 'components/Ted'
import Banner from 'components/Banner'
import NavComp from 'components/NavComp'
import RankWrap from 'components/RankWrap'
import TopHeader from 'components/TopHeader'
import FooterComp from 'components/FooterComp'

export default {
  name: 'app',
  components: {
    Ted,
    Banner,
    NavComp,
    RankWrap,
    TopHeader,
    FooterComp
  },
  created () {
    // 隐藏初始化加载图标
    const $fullLoading = document.querySelector('.full-loading')
    $fullLoading && ($fullLoading.style.display = 'none')
  }
}
</script>
