<template>
  <div id="app">
    <!-- <img src="./assets/img/1.iichiko-首页.jpg" alt=""> -->
    <li class="home"><router-link  to="/home">iichiko(首页)</router-link></li>
    <li class="about"><router-link  to="/about">关于我们</router-link></li>
    <li class="product"><router-link  to="/product">商品详情</router-link></li>
    <li class="iichiko"><router-link  to="/iichiko">探索iichiko</router-link></li>
    <li class="news"><router-link  to="/news">最新情报</router-link></li>
    <li class="contact"><router-link  to="/contact">联系我们</router-link></li>
    <router-view/>
  </div>
</template>

<style>
  img{
    width:1600px;
  }
  li{
    list-style: none;
    background-color: #fff;
    border:1px solid #000;
    padding: 5px;
    position: absolute;
  }
  .router-link-active {    
    text-decoration: none;
    color: #000;
  }
  a{
    text-decoration: none;
    color: #000;
  }
  .home{
    top:100px;
    left:160px;
  }
  .about{
    top:100px;
    left:310px;
  }
  .product{
    top:100px;
    left:430px;
  }
  .iichiko{
    top:100px;
    left:540px;
  }
  .news{
    top:100px;
    left:680px;
  }
  .contact{
    top:100px;
    left:800px;
  }
  .jp{
    top:100px;
    left:1020px;
  }
  .search{
    top:120px;
    left:1300px;
  }
  
</style>


<script>

export default{
  
  mounted () {
    window.addEventListener('scroll', this.scrollToTop)
  },
  destroyed () {
    window.removeEventListener('scroll', this.scrollToTop)
  },
  
  
  methods: {
    // 点击图片回到顶部方法，加计时器是为了过渡顺滑
    backTop () {
        const that = this
        let timer = setInterval(() => {
          let ispeed = Math.floor(-that.scrollTop / 5)
          document.documentElement.scrollTop = document.body.scrollTop = that.scrollTop + ispeed
          if (that.scrollTop === 0) {
            clearInterval(timer)
          }
        }, 16)
    },
  
    // 为了计算距离顶部的高度，当高度大于60显示回顶部图标，小于60则隐藏
    scrollToTop () {
      const that = this
      let scrollTop = window.pageYOffset || document.documentElement.scrollTop || document.body.scrollTop
      that.scrollTop = scrollTop
      if (that.scrollTop > 60) {
        that.btnFlag = true
      } else {
        that.btnFlag = false
      }
    }
  }
}
</script>
