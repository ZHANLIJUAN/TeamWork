<template>
  <div class="nav">
    <div class="nav_1" @click="net()">
      <img src="~images/nav/image1.png">
      <p>IT·互联网</p>
    </div>
    <div class="nav_2" @click="design()">
      <img src="~images/nav/image2.png">
      <p>设计·创作</p>
    </div>
    <div class="nav_3" @click="language()">
      <img src="~images/nav/image3.png">
      <p>语言·留学</p>
    </div>
    <div class="nav_4" @click="job()">
      <img src="~images/nav/image4.png">
      <p>职业·考证</p>
    </div>
    <div class="nav_5" @click="study()">
      <img src="~images/nav/image5.png">
      <p>升学·考研</p>
    </div>
    <div class="nav_6" @click="hobby()">
      <img src="~images/nav/image6.png">
      <p>兴趣·生活</p>
    </div>
  </div>
</template>

<script>
import 'style/NavComp.less'

export default {
  name: 'nav-comp',
  methods: {
    net () {
      window.location.href = 'http://www.baidu.com'
    },
    design () {
      window.location.href = 'http://www.duzhe.com'
    },
    language () {
      window.location.href = 'http://www.souhu.com'
    },
    job () {
      window.location.href = 'http://www.sina.com'
    },
    study () {
      window.location.href = 'http://www.tianya.com'
    },
    hobby () {
      window.location.href = 'http://www.yahoo.com.cn'
    }
  }
}
</script>
