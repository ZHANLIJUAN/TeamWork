<template>
  <header class="top-header">
    <div class="topbox">
      <p class="header-logo" v-show="searchlogo"></p>
      <div class="header-search" :class="{ 'searchopen': !searchlogo }">
        <i class="search-logo"></i>
        <input
          type="text"
          class="search-input"
          v-model="searchText"
          @focus="inputfoucs"
          @keyup.enter.prevent="handleSearch()"
          placeholder="搜索课程/老师/机构"
        />
      </div>
      <div class="header-navlist" v-show="searchlogo" @click="mainshow(mainfalg)">
        <ul class="main-navlist" :class="{ 'mainopen':mainfalg }">
          <li
            v-for="list in mainlist"
            @click.stop="mainclick"
          >
            <i class="listicon"></i>
            <span>{{ list }}</span>
          </li>
        </ul>
      </div>
      <div class="u-search-btn" v-show="!searchlogo" @click="inputblur">取消</div>
    </div>
    <div class="search-page" v-bind:class="{ 'pageopen': !searchlogo }">
      <div class="search-page-list">
        <h2 class="hottit">
  						<i></i>
  						热门搜索
  					</h2>
        <ul class="search-page-gotlist">
          <li
            v-for="item in gotlist"
            :class="{ 'hotred': item.hot}"
            @touchend.stop="handleSearch(item.text)"
          >
            {{ item.text }}
          </li>
        </ul>
      </div>
    </div>
    <div class="maskbg" v-show="maskshowtime" @click="maskchange()"></div>
  </header>
</template>

<script>
import 'style/TopHeader.less'

export default {
  name: 'top-header',
  data () {
    return {
      searchText: '',
      maskshowtime: false,
      searchlogo: true,
      mainfalg: false,
      gotlist: [{
        text: '产品学院',
        hot: true
      }, {
        text: '雅思',
        hot: false
      }, {
        text: 'PPT',
        hot: false
      }, {
        text: '韩语',
        hot: false
      }, {
        text: 'ps',
        hot: false
      }, {
        text: '设计',
        hot: false
      }, {
        text: '摄影',
        hot: false
      }, {
        text: '考研政治',
        hot: false
      }],
      mainlist: [
        '发现',
        '学团',
        '学习计划',
        '我的'
      ]}
  },
  methods: {
    inputfoucs: function () {
      this.mainfalg = false
      this.maskshowtime = true
      this.searchlogo = false
    },
    inputblur: function () {
      this.maskshowtime = false
      this.searchlogo = true
    },
    mainshow: function (mainfalg) {
      if (this.maskshowtime) {
        this.maskshowtime = false
      } else {
        this.maskshowtime = true
      }
      this.mainfalg = !mainfalg
    },
    mainclick: function (mainfalg) {
      this.maskshowtime = false
      this.mainfalg = !mainfalg
    },
    maskchange: function () {
      this.maskshowtime = false
      this.searchlogo = true
      this.mainfalg = false
    },
    handleSearch (text) {
      window.location.href = `http://m.ke.qq.com/courseList.html?_bid=167&_wv=1025&word=${text || this.searchText}`
    }
  }
}
</script>
