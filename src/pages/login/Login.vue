<template>
  <div class="main">
    <div class="header">
      <div class="header-center fl">
        <div class="header-title">
          综合检测平台
        </div>
        <div class="header-img"></div>
      </div>
      <div class="header-bottom fl"></div>

    </div>

    <div class="content">
      <div class="content-left">
        <!--<img src="images/d.png" alt="">-->
      </div>
      <div class="content-right">
        <div class="right-infp">
          <div class="right-infp-name">

            <input type="text" name="username" placeholder="请输入用户名" maxlength="12" required="" value=""
                   autocomplete="off">
          </div>
          <div class="right-infp-name">
            <input type="password" name="name" placeholder="请输入密码" autocomplete="off">
          </div>

          <div class="right-infp-btn">
            <button @click="login" class="btn">登录</button>
          </div>
        </div>
      </div>
    </div>


  </div>
</template>

<script>
export default {
  name: 'Login',
  data () {
    return {}
  },
  mounted () {
    let htmlDom = document.getElementsByTagName('html')[0]
    htmlDom.style.fontSize = `${htmlDom.clientWidth / 24}px`
  },
  methods: {
    login () {
      this.$router.push('/')
    }
  }
}

</script>
<style scoped>
@import './login.css';
</style>


