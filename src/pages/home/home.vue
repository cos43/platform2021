<template>
  <div>
    <div class="main">
      <div class="header">
        <div class="header-left fl" id="time"></div>
        <div class="header-center fl">
          <div class="header-title">
            综合检测平台
          </div>
          <div class="header-img"></div>
        </div>
        <div class="header-right fl"></div>
        <div class="navs">
          <div class="nav-item">
            首页
          </div>
          <div @click="currentFrame='honeypot'" class="nav-item">
            蜜罐
          </div>
          <div @click="currentFrame='AssociationAnalysis'" class="nav-item">
            关联分析
          </div>
          <div @click="currentFrame='knowledgeGraph'" class="nav-item">
            知识图谱
          </div>
          <div @click="currentFrame='maliciousCodeAnalysis'" class="nav-item">
            恶意代码分析
          </div>

        </div>
        <div class="header-bottom fl">

        </div>

      </div>
      <div class="home-content">
        <div class="frame-header">
          <svg @click="redirect" t="1639124199889" class="icon" viewBox="0 0 1024 1024" version="1.1"
               xmlns="http://www.w3.org/2000/svg"
               p-id="3608" width="128" height="128">
            <path
                d="M554.666667 494.933333l-29.866667-29.866666 89.6-89.6 29.866667 29.866666-89.6 89.6zM494.933333 554.666667l-123.733333 123.733333-29.866667-29.866667 123.733334-123.733333 29.866666 29.866667z m93.866667-34.133334l29.866667-29.866666 51.2 51.2 170.666666-170.666667-179.2-179.2-170.666666 170.666667 38.4 38.4-29.866667 29.866666L426.666667 358.4 657.066667 128l243.2 243.2-230.4 230.4-81.066667-81.066667z m-157.866667-25.6l-29.866666 29.866667-38.4-38.4-170.666667 170.666667 179.2 179.2 170.666667-170.666667-51.2-51.2 29.866666-29.866667 81.066667 81.066667L371.2 896 128 657.066667 358.4 426.666667l72.533333 68.266666z"
                fill="#1296db" p-id="3609"></path>
          </svg>

          <svg @click="fullScreen" t="1639123754166" class="icon" viewBox="0 0 1024 1024" version="1.1"
               xmlns="http://www.w3.org/2000/svg"
               p-id="2294" width="128" height="128">
            <path
                d="M358.4 768H426.666667v85.333333H213.333333v-213.333333h85.333334v68.266667l128-128 59.733333 59.733333-128 128z m345.6 0l-128-128 59.733333-59.733333 132.266667 132.266666V640h85.333333v213.333333h-213.333333v-85.333333h64zM358.4 298.666667l128 128-59.733333 59.733333-128-128V426.666667H213.333333V213.333333h213.333334v85.333334H358.4z m345.6 0H640V213.333333h213.333333v213.333334h-85.333333V354.133333l-132.266667 132.266667-59.733333-59.733333 128-128z"
                fill="#1296db" p-id="2295"></path>
          </svg>
        </div>
        <iframe allowtransparency="true" :src="frameList[currentFrame]" border="none">

        </iframe>
      </div>
    </div>
    <div class="fullScreen" v-if="showFullScreen">
      <div class="frame-header">
        <svg @click="redirect" t="1639124199889" class="icon" viewBox="0 0 1024 1024" version="1.1"
             xmlns="http://www.w3.org/2000/svg"
             p-id="3608" width="128" height="128">
          <path
              d="M554.666667 494.933333l-29.866667-29.866666 89.6-89.6 29.866667 29.866666-89.6 89.6zM494.933333 554.666667l-123.733333 123.733333-29.866667-29.866667 123.733334-123.733333 29.866666 29.866667z m93.866667-34.133334l29.866667-29.866666 51.2 51.2 170.666666-170.666667-179.2-179.2-170.666666 170.666667 38.4 38.4-29.866667 29.866666L426.666667 358.4 657.066667 128l243.2 243.2-230.4 230.4-81.066667-81.066667z m-157.866667-25.6l-29.866666 29.866667-38.4-38.4-170.666667 170.666667 179.2 179.2 170.666667-170.666667-51.2-51.2 29.866666-29.866667 81.066667 81.066667L371.2 896 128 657.066667 358.4 426.666667l72.533333 68.266666z"
              fill="#1296db" p-id="3609"></path>
        </svg>
        <svg @click="exitFullscreen" t="1639127009360" class="icon" viewBox="0 0 1024 1024" version="1.1" xmlns="http://www.w3.org/2000/svg" p-id="8153" width="128" height="128"><path d="M298.666667 631.466667H226.133333v-81.066667h217.6v204.8h-85.333333v-68.266667l-128 128L170.666667 759.466667l128-128z m422.4 0l128 128-59.733334 59.733333-128-128v68.266667h-85.333333V554.666667h217.6v81.066666h-72.533333zM298.666667 341.333333L187.733333 230.4 243.2 170.666667l115.2 115.2V217.6h85.333333v204.8H226.133333V341.333333H298.666667z m430.933333 0h64v81.066667h-217.6V217.6h85.333333v72.533333L780.8 170.666667l59.733333 59.733333L729.6 341.333333z" fill="#1296db" p-id="8154"></path></svg>

      </div>
      <iframe allowtransparency="true" class="fullScreenIframe" :src="frameList[currentFrame]" border="none">

      </iframe>
    </div>
  </div>
</template>
<script>
export default {
  name: 'Home',
  data () {
    return {
      frameList: {
        'baidu': 'https://webvpn.bupt.edu.cn/login',
        'honeypot': 'https://10.112.254.160:61280/login',
        'AssociationAnalysis': 'http://10.112.254.160:12125/www/session/login.php',
        'knowledgeGraph': 'http://10.128.222.213:8080/',
        'maliciousCodeAnalysis': 'https://10.112.254.160:10002/'
      },
      currentFrame: 'baidu',
      showFullScreen: false
    }
  },
  mounted () {
    let htmlDom = document.getElementsByTagName('html')[0]
    htmlDom.style.fontSize = `${htmlDom.clientWidth / 24}px`
  },
  methods: {
    getCurrentFrame () {
      return this.frameList[this.currentFrame]
    },
    fullScreen () {
      this.showFullScreen = true
    },
    exitFullscreen () {
      this.showFullScreen = false
    },
    redirect () {
      window.location.href = this.getCurrentFrame()
    }
  }
}
</script>
<style scoped>
@import './home.css';
</style>
